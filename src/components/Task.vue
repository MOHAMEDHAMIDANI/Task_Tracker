<template>
    <div class="task" :class="{'reminder' : task.reminder }">
        <div class="">
            <h3>{{ task.text }} <Button @click="delete_task(task.id)"  color="red" text="delete" /></h3>
            <h5>{{ task.day }}</h5>
        </div>
    </div>
</template>
<script lang="js">
import Button from "./Button"
export default {
    name: "Task",
    props: ["task"],
    components: {
        Button
    },
    methods: {
        delete_task(id) {
            this.$emit('delete_task', id)
        }
    }
}
</script>
<style scoped>
.task {
    background-color: #babbbc;
    margin: 5px;
    margin-bottom: 10px;
    padding: 10px 20px;
}
.reminder {
    border-left: 5px solid green;
}
.task h3 {
    color: black;
    display: flex;
    justify-content: space-between;
    align-items: center;
}
</style>