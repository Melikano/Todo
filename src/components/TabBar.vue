<template>
  <span>
    <button
      v-for="tab in tabs"
      :key="tab"
      @click="$emit('on-tab-changed', tab)"
    >
      {{ tab }}
    </button>
  </span>
</template>

<script lang="ts">
import Vue, { PropType } from "vue";
export default Vue.extend({
  name: "TabBar",
  props: {
    tabs: Array as PropType<Array<string>>,
  },
});
</script>
