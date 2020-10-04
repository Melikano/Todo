<template>
  <div>
    <todo-list :todos="todos" @click="toggleTodo" />
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import TodoList from "./TodoList.vue";

export default Vue.extend({
  name: "Todo",
  components: {
    TodoList,
  },
  data: () => ({
    todos: [
      { id: "1", text: "get-milk", done: false },
      { id: "2", text: "study", done: false },
    ],
  }),
  methods: {
    toggleTodo: function(todoId: string) {
      this.todos
        .filter((todo) => todo.id === todoId)
        .map((todo) => (todo.done = !todo.done));
    },
  },
});
</script>

<style scoped></style>
