<template>
  <h3 class="text-xl font-bold">{{ task.title }}</h3>
  <div class="flex gap-3 text-right">
    <i
      @click="taskStore.deleteTask(task.id)"
      class="material-icons cursor-pointer text-gray-300 hover:text-gray-400"
      >delete</i
    >
    <i
      @click="taskStore.toggleFav(task.id)"
      class="material-icons cursor-pointer text-gray-300 hover:text-gray-400"
      :class="{ 'text-red-500 hover:text-red-600': task.isFav }"
      >favorite</i
    >
  </div>
</template>

<script setup>
import { useTaskStore } from "../stores/TaskStore";

const props = defineProps({
  task: Object,
});

const taskStore = useTaskStore();
</script>
