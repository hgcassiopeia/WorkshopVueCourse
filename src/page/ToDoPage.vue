<template>
    <div class="container">
        <div class="task-zone">
            <div class="drop-zone">
                <h1>To-Do</h1>
                <div class="drag-el" >
                    Item A
                </div>
            </div>
            <div class="drop-zone">
                <h1>Doing</h1>
                <div class="drag-el" >
                    Item B
                </div>
            </div>
            <div class="drop-zone">
                <h1>Done</h1>
                <div class="drag-el" >
                    Item C
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'ToDoPage'
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