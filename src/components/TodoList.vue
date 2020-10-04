<template>
  <ul>
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
.done {
  text-decoration: line-through;
}
</style>
