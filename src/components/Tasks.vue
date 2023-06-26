<template>
    <div v-bind:key="task.id" v-for="task in tasks">
        <Task @delete_task="delete_task(task.id)" :task="task"/>
</div>
</template>

<script lang="js">
import Task from './Task'
export default {
    name: "Tasks",
    props: ["tasks"],
    components: {
        Task 
    },
    methods: {
        delete_task(id) {
            this.$emit("delete_task",id)
        }
    }
    ,
    emits:["delete_task",]
}
</script>