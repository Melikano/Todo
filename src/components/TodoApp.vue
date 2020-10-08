<template>
  <div>
    <todo-list :todos="todos" @click="toggleTodo">
      <template #title><h3>what to do today</h3></template>
    </todo-list>
    <add-todo @submit="addNewTodo" />
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import TodoList from "./TodoList.vue";
import AddTodo from "./AddTodo.vue";

export default Vue.extend({
  name: "Todo",
  components: {
    TodoList,
    AddTodo,
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
    addNewTodo: function(todoText: string) {
      const id = (this.todos.length + 1).toString();
      this.todos = [...this.todos, { id, text: todoText, done: false }];
    },
  },
});
</script>

<style scoped></style>
