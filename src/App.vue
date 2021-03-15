<template>
<div class="container">
<Header title="Task Tracker"/>
<div v-if="showAddTask">
<Form/>  
</div>
<Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks"/>

</div>
</template>

<script>
 
import Header from "./components/Header"
import Tasks from "./components/Tasks"
import Form from "./components/Form"

export default {
  name: "App",
  components: {
    Header,
    Tasks,
    Form,
  },
  data(){
    return{
      tasks:[],
      showAddTask:true
    }
  },
  methods:{
    deleteTask(id){
      if(confirm('Are you Sure?')){
        this.tasks= this.tasks.filter((task) => task.id !==id)
      }},
         toggleReminder(id){
           this.tasks= this.tasks.map((task)=>
           task.id ===id? {...task, reminder: !task.reminder}:task)
      }
  },
  created(){
    this.tasks=[
      {
        id:1,
        text:"Doctors Appointment",
        day: "March 1st at 2:30pm",
        reminder:true
      },
      {
        id:2,
        text:"Doctors Appointment",
        day: "March 1st at 2:30pm",
        reminder:true
      },
      {
        id:3,
        text:"Doctors Appointment",
        day: "March 1st at 2:30pm",
        reminder:true
      },
    ]
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
