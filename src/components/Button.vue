<template>
    <button @click="addTask()" :style="{background: color}" class="btn">{{text}}</button>
</template>

<script>
    export default {
        name: 'Button',
        props: {
            text: {
                type: String,
                default: "Click",
            },
            color: {
                type: String,
                default: "#000",
            }
        },

        methods: {
            addTask(){
                this.$emit("btn-click")
            }

        }
    }
</script>