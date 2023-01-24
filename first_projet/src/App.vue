<script>
// import HelloWorld from './components/HelloWorld.vue'
// import TheWelcome from './components/TheWelcome.vue'
import Tasks from './components/Tasks.vue'; 
export default {
  name :"app",
  components : {Tasks},

  data() {
    return {
      title: "Tasks Apps",
      newTask:null,
      tasks: [
        {
          body: 'Go to home',
          completed: false
        },
        {
          body: 'Go to sliping',
          completed: false
        },
        {
          body: 'Go to youcode',
          completed: false
        },
        {
          body: 'Go to shoping',
          completed: false
        },
        {
          body: 'Go to play',
          completed: false
        }
      ]
    };
  },

  methods: {
    addNewTask() {
      // console.log("add new task");
      this.tasks.push({
        body: this.newTask,
        completed: false
      });
      this.newTask = null;
    },
    completeTask(task) {
      task.completed = !task.completed; 
    },
    deleteTask(index) {
      // console.log('delete task'+ index);
      this.tasks.splice(index,1);
    }
  }
};
</script>

<template>
  
 <div id="app">
  <h1>Hello Jelouani Abdelghani !!</h1>
  <h3>{{ title }}</h3>
  <Tasks :tasks="tasks" v-on:completeTaskEvent="completeTask" v-on:deleteTaskEvent="deleteTask"></Tasks>
  <input @keyup.enter="addNewTask" type="text" class="form-control mb-2" v-model="newTask">
  <button v-on:click="addNewTask" class="btn btn-success btn-block"> Add New Task</button>
 </div>
 
</template>

<style>
.card{
  padding: 20px;
  background: #eee;
}
</style>
