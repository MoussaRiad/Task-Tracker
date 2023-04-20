<script>
import Header from './components/Header.vue';
import Footer from './components/Footer.vue';
import Tasks from './components/Tasks.vue';
import AddTask from './components/AddTask.vue';
export default {
  name: 'App',
  components: {
    Header,
    Footer,
    Tasks,
    AddTask
  },
  data(){
    return{
      tasks:[],
      showForm:false,
    }
  },
  computed:{
    tasksCount(){
      return this.tasks.length
    },
    modalStyle(){
      return this.showForm? 'block':'none';
    }
  },
  methods:{
    toggleForm(){
      this.showForm=!this.showForm
    },
    closeForm(){
      this.showForm=false
    },
    addTask(newTask){
      this.tasks=[...this.tasks,newTask]
      this.closeForm()

    },
    deleteTask(id){
      this.tasks=this.tasks.filter((task)=>task.id!=id)
      console.log('task',id)
    },
    toggleTask(id){
      this.tasks=this.tasks.map((task)=>task.id==id? {...task,reminder:!task.reminder}:task)
    }
  },
  created(){
    this.tasks=[
    {
          id:1,
          text:'Doctors Appointment',
          day:'Feb 5th at 2:30pm',
          reminder:true,
        },
        {
          id:2,
          text:'Meeting at School',
          day:'Feb 6th at 1:30pm',
          reminder:true,
        },
        {
          id:3,
          text:'Food Shopping',
          day:'Feb 5th at 2:30pm',
          reminder:false,
        },
    ]
  },
}
</script>
<template>
  <div class="app">
    <Header @toggleForm="toggleForm"/>
    <main>
      <!-- <div :style="{display: 'block', position:'relative'}"> -->
      <div id="modal" class="modal" :style="{display: modalStyle}">
        <AddTask @close="closeForm" @add-task="addTask" :style="{}"/>
      </div>
      <Tasks @toggle-reminder="toggleTask" @delete-task="deleteTask" :tasks="tasks"/>
    </main>
    <Footer />
  </div>
</template>

<style>
*{
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}
input::selection{
  
}
.app{
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  width: 100%;
  justify-content: center;
  align-items: center;
  padding: 0;
  transition: all ease .5s;
}
.app.disabled{
  opacity: .5;

}
main{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
}
.modal{
  position: fixed;
  z-index: 1;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  overflow: auto;
  background-color: rgba(0,0,0,0.4); /* Black w/ opacity */
}
</style>
