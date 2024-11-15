<script setup lang="ts">
import {
  ref,
  onBeforeMount,
  onMounted,
  onBeforeUpdate,
  onUpdated,
  onBeforeUnmount,
  onUnmounted,
} from "vue";

const count = ref(0);

onBeforeMount(() => {
  console.log("Before Mount Hook is called");
});

onMounted(() => {
  console.log("Mount Hook is called");
});

onBeforeUpdate(() => {
  console.log("Before Update Hook is called");
});

onUpdated(() => {
  console.log("Updated Hook is called");
});

onBeforeUnmount(() => {
  console.log("Before Unmount Hook is called");
});

onUnmounted(() => {
  console.log("Unmounted Hook is called");
});
</script>

<template>
  <div>
    <h2>Practice Life Cycle Hook's of Vue Js</h2>
    <button class="border border-red-300 px-4 py-2 rounded-xl" @click="count++">
      {{ count }}
    </button>
  </div>
</template>
