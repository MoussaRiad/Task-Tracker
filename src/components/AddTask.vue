<template>
    <div class="add-task">
        <span @click="$emit('close')" ref="span" class="close">&times;</span>
        <form class="add-form" @submit="submit">
            
            <div class="form-header">
                <h3>Add a Task</h3>
            </div>
            <div class="form-controller">
                <label>Task</label>
                <input v-model="text" type="text" name="text" placeholder="Add a Task"/>
                <!-- {{ text }} -->
            </div>
            <div class="form-controller">
                <label>Date</label>
                <input v-model="day" type="date" name="day" placeholder="Day & Time"/>
                <!-- {{ day }} -->
            </div>
            <div class="form-controller">
                <label>Reminder</label>
                <input v-model="reminder" type="checkbox" name="reminder"/>
            </div>
            <button :disabled="disabled" :style="{background: 'green',width:'100%'}" class="btn" type="submit">Save Task</button>
        </form>
    </div>
</template>

<script>
// import { ref, onMounted } from 'vue'

// const span = ref();
// const modal = document.getElementById("modal");
// onMounted(() => {
//     console.log('span mounted',span);
//     span.addEventListener("click",function() {
//         modal.style.display = "none";
//         console.log("span clicked");
//     })
// })
    export default {
        name:'AddTask',
        props:{},
        computed:{
            disabled(){
                console.log(toString(this.day.length))
                return (this.text.length<10 && this.day );
            }
        },
        methods:{
            submit(e){
                e.preventDefault();
                const newTask={
                    id:Math.floor(Math.random()*10000),
                    text:this.text,
                    day:this.day,
                    reminder:this.reminder
                };
                this.$emit('add-task',newTask);
                this.text='';
                this.day=toString(Date.day);
                this.reminder=false;
            },
        },
        data(){
            return{
                text:'',
                day:toString(Date.now),
                reminder:false,
            }
        },
        created(){
            this.day=toString(Date.now)
        }
    }
</script>

<style scoped>
.add-task{
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 10px 20px;
    margin: 20px auto;
    width: 500px;
    z-index: 10;
    box-shadow: 0 0 8px 0 black;
    border-radius: 5px;
    background-color: #fefefe;
    animation-name: animatetop;
    animation-duration: 0.4s
}

/* Add Animation */
@keyframes animatetop {
  from {top: -300px; opacity: 0}
  to {top: 0; opacity: 1}
}
.close{
    position: absolute ;
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
    top: 5px;
    right:  10px;
    font-size: 14px;
    cursor: pointer;
    border-radius: 50%;
    width: 35px;
    height: 35px;
    color: red;
    transition: all ease .5s;
}
.close:hover{
    color: white;
    background-color: rgba(255, 0, 0, 0.475);
}
.form-header{
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 10px 0;
    font-weight: bold;
}
.form-header::after{
    content: '';
    position: absolute;
    display: block;
    width: 100%;
    height: 2px;
    background-color: lightseagreen;
    margin: 10px 0;
    top: 10px;
}
.form-header h3{
    position: relative;
    z-index: 1;
    font-size: 20px;
    color: lightseagreen;
    background-color: #fefefe;
    padding: 0 10px;
}
.form-controller:nth-child(-n+3){
    display: flex;
    flex-direction: column;
    justify-content: space-evenly
}
.form-controller label{
    color: lightseagreen;
    font-size: 15px;
}
.form-controller:nth-child(-n+3) input{
    width: 350px;
    height: 40px;
    border-radius: 5px;
    border: solid 2px lightgrey;
    padding: 0 10px;
    margin: 10px auto;
    transition: all ease .5s;
}
.form-controller:nth-child(-n+3) input:focus{
    /* border-style: none; */
    border: solid 2px lightseagreen;
    font-size: 15px;
    outline: none;
}
.form-controller:nth-child(4){
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-top: 30px;
    padding: 10px 20px;
}

.form-controller:nth-child(4) input{
    height: 20px;
    width: 20px;
    transition: all ease .5s;
}
.add-form .btn::before{
    left: -40px;
}
.add-form .btn:hover::before{
        transform: skew(-45deg) translateX(410px);
}
</style>