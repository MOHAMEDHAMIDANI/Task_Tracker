<template>
    <header>
        <h1> {{ title }}</h1>
        <Button @click="$emit('show_add')" 
        :color="showAddTask ? 'red': 'green'"
        :text="showAddTask ? 'close':'add task'"/>
    </header>
</template>
<script>
import Button from './Button'

    export default {
    name: "header",
    props: ['title',"showAddTask"],
    components: {
        Button
    },
    methods: {
        add() {
            this.$emit('show_add')
        }
    }
}

</script>

<style >
    header {
        display: flex;
        justify-content: space-between;
        align-content: center;
        margin-bottom: 20px; 
    }
</style>