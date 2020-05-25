<template>
    <div class="container">
        <div class="card" v-for="archive in archives" :key="archive.id">
            <h3>{{ archive.date }} : {{ archive.time }}</h3>
            <ul v-for="task in archive.tasks" :key="task.id">
                <li>{{ task.id }} - {{ task.title }}</li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    name: 'CardList',
    props: ['archives']
}
</script>

<style scoped>
h3{
    border-bottom: 1px solid gray;
    padding-bottom: 10px;
}
.card{
    background-color :#ffffff;
    width: 50%;
    height: auto;
    border: 1px solid gray;
    border-radius: 10px;
    margin: 10px auto;
}
li{
    list-style: none;
}
</style>