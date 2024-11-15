<script setup lang="ts">
import { defineProps } from "vue";

const { title, count } = defineProps(["title", "count"]);

console.log("title props :", title);
</script>

<template>
  <div class="border border-blue-300 p-4 m-4 bg-slate-400">
    <h4>This is child component: {{ title }}</h4>
    <h5>Clicked me {{ count }} times</h5>
  </div>
</template>
