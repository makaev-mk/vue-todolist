<template>
  <app-header @add-task="addUncompleted"></app-header>
  <div class="container content">
    <!-- Uncompleted tasks -->
    <todo-list :tasks="tasks"
               @removeTask="removeTodo"
               @compData="upCompleted"
    ></todo-list>
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader";
import TodoList from "@/components/TodoList";

export default {
  data() {
    return {
      tasks: [],
    }
  },
  name: 'App',
  components: { AppHeader, TodoList },
  methods: {
    addUncompleted(value) {
      this.tasks.push(value)
    },
    removeTodo(id) {
      this.tasks = this.tasks.filter(item => item.id != id)
    },
    upCompleted(id) {
      this.tasks.forEach(item => {
        if (item.id === id) {
          if (!item.completed) {
            item.completed = 1
          } else {
            item.completed = 0
          }
        }
      })

      this.tasks.sort(function(a,b){return b.completed-a.completed})
      console.log(this.tasks)
    },
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
</style>
