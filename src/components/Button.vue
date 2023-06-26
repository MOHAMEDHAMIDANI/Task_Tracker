<template>
    <button v-bind:style="{ background: color }" class="btn">{{ text }}</button>
</template>

<script lang="js">

export default {
    name: "btn",
    props: ['text', 'color'],
    methods: {
        onclick() {
            console.log("fuck you iam working ");
        }
    }
}
</script>