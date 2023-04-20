<template>
    <div @dblclick="$emit('toggle-reminder',task.id)" :class="[task.reminder? 'reminder':'','task']">
        <h3>{{ task.text }}
            <i @click="$emit('delete-task',task.id)" class="fas fa-times"></i>
        </h3>
        <p>{{ task.day }}</p>
    </div>
</template>

<script>
    export default{
        name :"Task",
        props:{
            task:Object,
        },
        emits:[
            'delete-task','toggle-reminder'
        ]
    }
</script>

<style scoped>
.task{
    background-color: #dfdfdf;
    min-width: 300px;
    padding: 10px 40px 10px 20px;
    margin: 10px auto;
    border-radius: 5px;
    border-left: solid 0px transparent;
    transition: all ease .5s;
}
.task:hover{
    opacity: .8;
    transform: scale(1.1,1.1);
}
.task.reminder{
    border-left: solid 8px lightgreen;
    transition: all ease .5s;
}
.task{
    cursor: pointer;
}
</style>