<template>
  <div>
    <todo-list :todos="filteredTodos" @click="toggleTodo">
      <template #title><h2>what to do today</h2></template>
    </todo-list>
    <add-todo @submit="addNewTodo" />
    <button @click="setFilter(filters.done)">done</button>
    <button @click="setFilter(filters.pending)">pending</button>
    <button @click="setFilter(filters.all)">all</button>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import TodoList from "./TodoList.vue";
import AddTodo from "./AddTodo.vue";
import type { VisibilityFilter } from '../types/types';
import { visibilityType } from '../constants/constants';

const filters = visibilityType;
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
    filters,
    filter: filters.all,
  }),
  computed:{
    filteredTodos: function(){
      switch(this.filter) {
        case visibilityType.done :
          return this.todos.filter(todo => todo.done);
        case visibilityType.pending :
          return this.todos.filter(todo => !todo.done)
        default :
          return this.todos;
      }
    }
  },
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
    setFilter: function(filter: VisibilityFilter){
      this.filter = filter;
    },
  },
});
</script>

<style scoped></style>
