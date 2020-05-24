<template>
    <div class="container">
        <div class="task-zone">
            <div class="drop-zone">
                <h1>To-Do</h1>
                <div class="drag-el" v-for="task in taskTodo" :key="task.id" >
                    {{ task.title }}
                </div>
            </div>
            <div class="drop-zone">
                <h1>Doing</h1>
                <div class="drag-el" v-for="task in taskDoing" :key="task.id" >
                    {{ task.title }}
                </div>
            </div>
            <div class="drop-zone">
                <h1>Done</h1>
                <div class="drag-el" v-for="task in taskDone" :key="task.id" >
                    {{ task.title }}
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'TaskList',
    data(){
        return{
            tasks:[
                {
                    id: 1,
                    title: 'Item A',
                    status: 'todo'
                },
                {
                    id: 2,
                    title: 'Item B',
                    status: 'doing'
                },
                {
                    id: 3,
                    title: 'Item C',
                    status: 'doing'
                },
                {
                    id: 4,
                    title: 'Item D',
                    status: 'done'
                }
            ]
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
    }
}
</script>

<style scoped>
.container{
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