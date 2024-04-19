<template>
  <form
    @submit.prevent="handleSubmit"
    class="mx-auto grid w-full max-w-sm grid-cols-4 gap-2.5"
  >
    <input
      type="text"
      placeholder="I need to..."
      v-model="newTask"
      class="col-span-3 rounded-md p-2.5 focus-visible:outline-yellow-300"
    />
    <button
      class="col-span-1 rounded-md bg-yellow-300 p-2.5 hover:bg-yellow-400"
    >
      Add
    </button>
  </form>
</template>

<script setup>
import { useTaskStore } from "../stores/TaskStore";
import { ref } from "vue";

const taskStore = useTaskStore();
const newTask = ref("");

const handleSubmit = () => {
  if (newTask.value.length > 0) {
    taskStore.addTask({
      title: newTask.value,
      isFav: false,
      id: Math.floor(Math.random() * 10000),
    });
    newTask.value = "";
  }
};
</script>
