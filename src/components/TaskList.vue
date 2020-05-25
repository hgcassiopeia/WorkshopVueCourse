<template>
    <div class="container">
        <div class="add-task">
            <input id="new-task" type="text" v-model="newTask">
            <button type="button" @click="addTask(newTask)">Add New Task</button>
        </div>
        <div class="task-zone">
            <div class="drop-zone" @drop="onDrop($event, 'todo')" @dragover.prevent @dragenter.prevent>
                <h1>To-Do</h1>
                <div class="drag-el" v-for="task in taskTodo" :key="task.id" draggable @dragstart="onStart($event, task)">
                    <span v-if="editTask != task.id">{{ task.title }}</span>
                    <input v-else class="edit-task" type="text" v-model="task.title">
                    <br>
                    <button v-if="editTask != task.id" type="button" @click="onEdit(task)">Edit</button>
                    <button v-else type="button" @click="editedTask(task)">Save</button>
                    <button type="button" @click="deleteTask(task.id)">Delete</button>
                </div>
            </div>
            <div class="drop-zone" @drop="onDrop($event, 'doing')" @dragover.prevent @dragenter.prevent>
                <h1>Doing</h1>
                <div class="drag-el" v-for="task in taskDoing" :key="task.id" draggable @dragstart="onStart($event, task)">
                    <span v-if="editTask != task.id">{{ task.title }}</span>
                    <input v-else class="edit-task" type="text" v-model="task.title">
                    <br>
                    <button v-if="editTask != task.id" type="button" @click="onEdit(task)">Edit</button>
                    <button v-else type="button" @click="editedTask(task)">Save</button>
                    <button type="button" @click="deleteTask(task.id)">Delete</button>
                </div>
            </div>
            <div class="drop-zone" @drop="onDrop($event, 'done')" @dragover.prevent @dragenter.prevent>
                <h1>Done</h1>
                <div class="drag-el" v-for="task in taskDone" :key="task.id" draggable @dragstart="onStart($event, task)">
                    <span v-if="editTask != task.id">{{ task.title }}</span>
                    <input v-else class="edit-task" type="text" v-model="task.title">
                    <br>
                    <button v-if="editTask != task.id" type="button" @click="onEdit(task)">Edit</button>
                    <button v-else type="button" @click="editedTask(task)">Save</button>
                    <button type="button" @click="deleteTask(task.id)">Delete</button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    name: 'TaskList',
    created(){
        this.getTask();
    },
    data(){
        return{
            newTask: "",
            editTask: "",
            tasks:[]
        }
    },
    computed:{
        taskTodo(){
            return this.tasks.filter(task => task.status === 'todo')
        },
        taskDoing(){
            return this.tasks.filter(task => task.status === 'doing')
        },
        taskDone(){
            return this.tasks.filter(task => task.status === 'done')
        }
    },
    methods:{
        onStart(e, task){
            e.dataTransfer.dropEffect = 'move'
            e.dataTransfer.effectAllowed = 'move'
            e.dataTransfer.setData('taskId', task.id)
        },
        onDrop(e, newStatus){
            const taskId = e.dataTransfer.getData('taskId')
            const task = this.tasks.find(task => task.id == taskId)
            task.status = newStatus
        },
        async getTask(){
            const { data } = await axios.get(`http://localhost:3000/tasks`)
            this.tasks = data
        },
        async addTask(newTask){
            const newTitle = newTask
            await axios.post(`http://localhost:3000/tasks`, { title: newTitle, status: 'todo' })
            this.getTask();
            this.newTask = "";
        },
        async deleteTask(taskId){
            await axios.delete(`http://localhost:3000/tasks/${taskId}`)
            this.getTask();
        },
        onEdit(task){
            this.editTask = task.id
        },
        async editedTask(updateTask){
            await axios.put(`http://localhost:3000/tasks/${updateTask.id}`, updateTask)
            this.editTask = null
            this.getTask();
        }
    }
}
</script>

<style scoped>
.container, .add-task{
    margin: 30px 0;
}
.task-zone{
    display: flex;
    justify-content: space-around;
}
.drop-zone{
    border: 1px solid black;
    border-radius: 10px;
    width: 250px;
    height: 400px;
    padding: 10px 0;
}
.drag-el{
    border: 1px solid black;
    width: 200px;
    height: 40px;
    border-radius: 10px;
    margin: 5px auto;
    padding-top: 15px;
}
</style>