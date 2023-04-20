<template>
    <button @click="$emit('btn-click')" :style="{background:color}" class="btn">{{ text }}</button>
</template>

<script>
    export default{
        name :"Button",
        props:{
            text:String,
            color:String,
            click:Function,
        },

    }
</script>

<style>
    .btn{
        border-radius: 5px;
        color: white;
        border: none;
        padding: 10px 20px;
        margin: 10px 0;
        transition: ease .5s;
        position: relative;
        overflow: hidden;
        cursor: pointer;

    }
    .btn:disabled{
        opacity: .3;
        cursor: not-allowed;
    }
    .btn::before{
        content: '';
        width: 10px;
        height: 100%;
        transform: skew(-45deg);
        position: absolute;
        background-color: rgba(236, 236, 236, 0.813);
        top: 0;
        left: -32px;
        /* z-index: 10; */

    }
    .btn:not(:disabled):hover{
        opacity: .8;
    }
    /* .btn:disabled:hover{} */
    .btn:not(:disabled):hover::before{
        transform: skew(-45deg) translateX(140px);
        transition: ease .4s;
    }
</style>