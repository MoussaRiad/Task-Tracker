<template>
    <div class="header">
        <h1>Task Tracker</h1>
        <Button @btn-click="this.$emit('toggleForm')" text="Add Task" color="green"/>
    </div>
</template>

<script>
    import Button from './Button.vue';
    export default {
        name:'Header',
        components:{
            Button,
        },
        methods : {
            
        }
    }
</script>

<style scoped>
    .header{
        display: flex;
        justify-content: space-evenly;
        align-items:center;
        border: none;
        box-shadow: 0 0 8px 0 rgba(0,0,0,0.5);
        width: 100vw;
        padding: 20px 0px;
        margin: 0 auto;
    }
</style>

