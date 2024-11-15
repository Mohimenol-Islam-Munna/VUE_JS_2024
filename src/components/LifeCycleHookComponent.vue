<script setup lang="ts">
import {
  ref,
  reactive,
  onBeforeMount,
  onMounted,
  onBeforeUpdate,
  onUpdated,
  onBeforeUnmount,
  onUnmounted,
} from "vue";
import axios from "axios";

const count = ref(0);
const userList = reactive({
  isLoading: false,
  data: null,
  error: null,
});

console.log("userList :", userList);

onBeforeMount(() => {
  console.log("Before Mount Hook is called");
});

onMounted(() => {
  console.log("Mount Hook is called");

  const fetcher = async () => {
    try {
      userList.isLoading = true;
      const res = await axios.get("https://jsonplaceholder.typicode.com/users");

      userList.data = res.data;
    } catch (err) {
      console.log("data fetching error: ", err);
      userList.error = err.response || err;
    } finally {
      userList.isLoading = false;
    }
  };

  fetcher();
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
    <div class="bg-white border border-yellow-300 my-8 p-5 rounded-xl">
      <div>
        <h2 v-if="userList.isLoading">Loading ...</h2>
        <h2 v-if="!userList.isLoading && userList.error" class="text-red-400">
          Something went wrong. Please try again
        </h2>
        <div v-if="!userList.isLoading && !userList.error && userList.data">
          <div v-for="(user, index) in userList.data">
            <h4 class="text-green-500">Name: {{ user.name }}</h4>
            <h6>Email: {{ user.email }}</h6>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
