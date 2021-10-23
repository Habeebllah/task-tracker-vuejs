<template>
  <div class="container">
    <Header @toggle-show-add-task="toggleShowAddTask" title="Task Tracker" :showAddTask="showAddTask"/>
    <div v-if="showAddTask">
      <AddTask @add-task="addTask"/>
    </div>
    <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks"/>
  </div>
</template>
C
<script>
import Header from './components/Header.vue'
import Tasks from './components/Tasks.vue'
import AddTask from './components/AddTask.vue'
export default {
  name: "App",
  components: {
    Header,
    Tasks,
    AddTask,
  },
  data(){
    return{
      tasks: [],
      showAddTask: false,
    }
  },
  methods: {
    deleteTask(id){
      if(confirm('Are you sure? ')){
          this.tasks = this.tasks.filter((task)=>task.id !==id)
      }
    },

    toggleReminder(id){
      this.tasks = this.tasks.map((task)=>task.id===id ? {...task, reminder: !task.reminder}: task)
    },

    addTask(task){
      this.tasks = [...this.tasks, task]

    },

    toggleShowAddTask(){
       this.showAddTask = !this.showAddTask
    }
  },
  created(){
    this.tasks = [
      {
        id: 1,
        text: 'Meeting at School',
        day: 'March 1st at 2:30pm',
        reminder: true,
      },
      {
        id: 2,
        text: 'Doctors Appointment',
        day: 'March 3rd at 1:30pm',
        reminder: false,
      },
      {
        id: 3,
        text: 'Food Shopping',
        day: 'March 6st at 5:30pm',
        reminder: true,
      },
      {
        id: 4,
        text: 'Driving at School',
        day: 'March 9st at 12:30pm',
        reminder: false,
      },
    ]
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap");

* {
  box-sizing: border-box;
  margin: 0;
}

body {
  font-family: "Poppins", sans-serif;
}

.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}

.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
</style>
