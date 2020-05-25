<template>
    <div>
        <CardList :archives="archives" />
    </div>
</template>

<script>
import CardList from '../components/CardList'
export default {
    name: 'ArchivePage',
    components: { CardList },
    data(){
        return {
            archives:[
                {
                    date: "22-05-2020",
                    time: "19:00",
                    tasks: [
                        { id: 1, title: "Item A", status: "done" },
                        { id: 2, title: "Item B", status: "done" },
                    ]
                },
                {
                    date: "24-05-2020",
                    time: "19:00",
                    tasks: [
                        { id: 1, title: "Item A", status: "done" },
                        { id: 2, title: "Item B", status: "done" },
                    ]
                }
            ]
        }
    }
}
</script>