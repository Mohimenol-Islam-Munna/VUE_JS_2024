<script setup lang="ts">
import { ref } from "vue";
import ChildComponent from "./ChildComponent.vue";

const title = "Child Component 100";
const count = ref(0);
</script>

<template>
  <div>
    <h2>Parent Component</h2>
    <button
      @click="count++"
      class="border border-red-400 px-4 py-2 rounded-md uppercase my-8"
    >
      click me
    </button>
    <ChildComponent title="Be a better component" :count="count" />
  </div>
</template>
