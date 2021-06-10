<template>
  <div id="app">
    <TasksList title="To do list"/>
    <form action="">
      <input type="text" v-model="userForm"/>
    </form>
      <button v-on:click="incrementTask">Ajouter</button>
    <div class="task" v-bind:key="task.id" v-for="task in tasks">
      <Task v-bind:title="task.title" v-bind:completed="task.completed"/>
    </div>
  </div>
</template>

<script>
import Task from './components/Task.vue';
import TasksList from './components/TasksList';
import axios from 'axios'

export default {
  name: 'App',
  components: {
    TasksList,
    Task,
  },
  data: function() {
    return{
        tasks: [],
        userForm: "",
        count : 0,
    }
    },
    methods:{
          incrementTask(){
            this.tasks.push({ id: this.tasks.length, title: this.userForm });
            this.userForm = "";
          }
    },
    mounted () {
      axios.get('https://jsonplaceholder.typicode.com/todos')
      .then(res => (this.tasks = res.data))
  }
}
</script>

<style>
body{
  background-color: #f7c600;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.task{
  background-color: rgba(220, 211, 108, 0.372);
  color: white;
  margin : 10px;
  padding: 10px;
}
.task--completed{
  background-color: #24de6851;
}
h1{
  color: white;
}
</style>
