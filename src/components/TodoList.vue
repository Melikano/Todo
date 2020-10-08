<template>
  <ul>
    <slot name="title">
      <h1>What to do on {{ new Date().toString().substring(0, 10) }}</h1>
    </slot>
    <li
      v-for="todo in todos"
      :key="todo.id"
      :class="todo.done ? 'done' : ''"
      @click="$emit('click', todo.id)"
    >
      {{ todo.text }}
    </li>
  </ul>
</template>

<script lang="ts">
import Vue, { PropType } from "vue";
import { Todo } from "../types/types";

const today = new Date();
console.log(today);
export default Vue.extend({
  name: "TodoList",
  props: {
    todos: {
      type: Array as PropType<Array<Todo>>,
      required: true,
    },
  },
});
</script>
<style scoped>
ul {
  list-style-type: none;
}
.done {
  text-decoration: line-through;
}
</style>
