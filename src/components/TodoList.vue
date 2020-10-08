<template>
  <ul>
    <slot name="title">
      <h2>What to do on {{ new Date().toString().substring(0, 10) }}</h2>
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

const today = new Date();
console.log(today);
export default Vue.extend({
  name: "TodoList",
  props: {
    todos: {
      type: Array as PropType<
        Array<{ id: string; text: string; done: boolean }>
      >,
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
