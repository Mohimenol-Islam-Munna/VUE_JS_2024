<script setup lang="ts">
import { ref, reactive } from "vue";
import LifeCycleHookComponent from "./components/LifeCycleHookComponent.vue";

const count = ref({
  amount: 100,
  income: {
    job: 100,
    freelance: 50,
    side_project: 20,
  },
});
const state = reactive({ count: 0 });

console.log("js portion state 1:", state.count);

function counterHandler() {
  count.value = {
    amount: 1200,
    income: {
      job: 1200,
      freelance: 520,
      side_project: 220,
    },
  };
}

function reactiveStateHandler() {
  state.count += 10;
}
</script>

<template class="border border-red-500">
  <div class="w-full max-w-[1024px] mx-auto bg-green-500 py-6 px-4">
    <h2 class="text-3xl text-red-500">This is first vue component</h2>
    <h6>Freelance Income: {{ count.income.freelance }}</h6>
    <button
      @click="counterHandler"
      class="px-5 py-3 border border-green-300 rounded-full"
    >
      Count {{ count.amount }}
    </button>
    <button
      @click="reactiveStateHandler"
      class="mx-3 px-5 py-3 border border-green-300 rounded-full"
    >
      Reactive Count {{ state.count }}
    </button>

    <div>
      <div v-if="state.count < 20">
        <LifeCycleHookComponent />
      </div>
      <div v-else><h2>LifeCycleHookComponent is unmounted</h2></div>
    </div>
  </div>
</template>
