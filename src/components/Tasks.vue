<template>
    <div class="tasks">
        <div v-for="task in tasks">
            <Task @toggle-reminder="$emit('toggle-reminder', task.id)" @delete-task="$emit('delete-task', task.id)"
                :task="task" />
        </div>
    </div>
</template>

<script>
import Task from './Task.vue';
export default {
    name: "Tasks",
    props: {
        tasks: Array,
    },
    components: {
        Task,
    },
    emits: [
        'delete-task', 'toggle-reminder'
    ]
}
</script>

<style scoped>
.tasks{
    border: solid 2px lightgreen;
    border-radius: 10px;
    padding: 20px 40px;
    margin: 20px auto;
    min-width: 300px;
}
</style>