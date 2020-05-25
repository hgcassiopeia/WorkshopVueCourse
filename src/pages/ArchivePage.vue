<template>
    <CardList :archives="archives" />
</template>

<script>
import axios from 'axios'
import CardList from '../components/CardList.vue'
export default {
    name: 'ArchivePage',
    components: { 
        CardList 
    },
    async created(){
        const { data } = await axios.get(`http://localhost:3000/archives`)
        this.archives = data
    },
    data(){
        return {
            archives: []
        }
    }
}
</script>