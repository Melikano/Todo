<template>
  <div>
    <input placeholder="add a todo" v-model="todoText" />
    <button @click="handleAddTodo">Add</button>
  </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  name: "AddTodo",
  data: () => ({
    todoText: "",
  }),
  methods: {
    handleAddTodo: function() {
      this.$emit("submit", this.todoText);
      this.todoText = "";
    },
  },
});
</script>
