<template>
<div :class="[task.reminder ? 'reminder' : '', 'task']">
    <h3 @click="$emit('dbl-toggle-reminder', task.id)">{{task.text}}
        <i @click="$emit('delete-task', task.id)" class="fas fa-times"></i>
    </h3>
    <p>{{task.day}}</p>
</div>
    
</template>

<script>
    
    export default {
        name: "Task",
        props: {
            task: Object,
        },
       
    }

    

</script>
    

<style scope>
.fas{
    color: red;
}
.task h3{
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.reminder{
    border-left: 5px solid green;
}

.task{
    background: #f4f4f4;
    margin: 5px;
    padding: 10px 20px;
    cursor: pointer;
}
</style>