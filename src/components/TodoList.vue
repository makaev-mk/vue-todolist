<template>
    <ul class="todo" id="todo">
      <component
          v-for="todo in tasks"
          :key="todo.id"
          :is="'app-todo'"
          v-bind="{text: todo.task, completed: todo.completed, id:todo.id}"
          @remove="emitData"
          @completed="emitCompleted"
      ></component>
    </ul>
</template>

<script>
import AppTodo from "@/components/AppTodo";

export default {
  emits: ['removeTask', 'compData'],
  props: ['tasks'],
  data(){
    return {
      }
  },
  methods: {
    emitData(id) {
      this.$emit('removeTask', id)
    },
    emitCompleted(id) {
      this.$emit('compData', id)
    }
  },
  components: {AppTodo}

}
</script>

<style scoped>

</style>
