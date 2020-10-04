<template>
  <div id="app">
    <todo-app />
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import TodoApp from "./components/TodoApp.vue";

export default Vue.extend({
  name: "App",
  components: {
    TodoApp,
  },
});
</script>

<style></style>
