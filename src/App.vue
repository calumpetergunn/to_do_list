<template>
  <div id="app">
    <ul>
      <li v-for="task, index in tasks" v-bind:key="index">
        <span v-bind:class="task.priority === 'high' ? 'high': 'low'">{{task.name}}</span>
      </li>
    </ul>

    <form class="form" v-on:submit.prevent="saveNewTask">
      <label for="new-task">Add a New Task:</label>
      <input type="text" id="new-task" v-model="newTask" required>
      <span>
        <input type="radio" id="high-priority" name="new-priority" value="high" v-model="newPriority" required>
        <label for="high-priority">High Priority</label>
      </span>
      <span>
        <input type="radio" id="low-priority" name="new-priority" value="low" v-model="newPriority">
        <label for="low-priority">Low Priority</label>
      </span>
      <input type="submit" value="Add Task">
    </form>
  </div>
</template>

<script>

export default {
  name: 'App',
  data () {
    return {
      tasks: [
        {name:"Vacuum", priority:"high" },
        {name:"Feed Hamster", priority: "low" },
        {name:"Wash Car", priority: "low" }
      ],
      newTask: "",
      newPriority: ""
    }
  }, 
  methods: {
  saveNewTask: function () {
    this.tasks.push(
      {name: this.newTask, priority: this.newPriority}
    );
    this.newTask = "";
    this.newPriority = ""
    }
  }
}
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

.high {
  color: red;
}

.low {
  color: green;
}

.form {
  display: flex;
  flex-direction: row;
  background-color: blanchedalmond;
  padding: 15px;
  border-radius: 15px;
}

.body {
  background-color: cornflowerblue;
}

.form > input, .form label {
  width: 15%;
  text-align: center;
  margin: 0px 10px 0px 10px;
}

#app > ul > li{
  list-style: none;
  background-color: whitesmoke;
  text-align: center;
  width: 25%;
}

ul {
  background-color: rgb(171, 209, 222);
  border-radius: 15px;
}

</style>
