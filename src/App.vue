<template>
  <div id="app">
    <!-- <ToDoPage /> -->
    <ArchivePage />
  </div>
</template>

<script>
// import ToDoPage from './pages/ToDoPage.vue'
import ArchivePage from './pages/ArchivePage.vue'

export default {
  name: 'App',
  components: {
    // ToDoPage,
    ArchivePage
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
