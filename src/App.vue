<template>
  <main>
    <!-- heading -->
    <header
      class="flex flex-col items-center justify-center bg-slate-200 pt-5 text-center"
    >
      <div class="flex items-center">
        <img
          src="https://upload.wikimedia.org/wikipedia/commons/1/1c/Pinialogo.svg"
          alt="pinia logo"
          class="max-w-14 -rotate-12"
        />
        <h1 class="ml-4 rotate-2 pt-6 text-3xl font-bold">Pinia Tasks</h1>
      </div>

      <!-- new task form -->
      <TaskForm class="py-5" />
    </header>

    <!-- filter -->
    <nav class="mx-auto my-2.5 max-w-2xl text-right">
      <button
        @click="filter = 'all'"
        class="ml-2.5 inline-block rounded border-2 border-solid border-gray-500 bg-white px-2 py-1"
      >
        All tasks
      </button>
      <button
        @click="filter = 'favs'"
        class="ml-2.5 inline-block rounded border-2 border-solid border-gray-500 bg-white px-2 py-1"
      >
        Fav tasks
      </button>
    </nav>

    <!-- task list -->
    <ul v-if="filter === 'all'" class="mx-auto my-5 max-w-2xl">
      <p>You have {{ taskStore.totalCount }} tasks left to do</p>
      <li
        v-for="task in taskStore.tasks"
        class="mt-5 flex items-center justify-between rounded bg-white p-5 shadow-md"
      >
        <TaskDetails :task="task" />
      </li>
    </ul>
    <ul v-if="filter === 'favs'" class="mx-auto my-5 max-w-2xl">
      <p>You have {{ taskStore.favCount }} favs left to do</p>
      <li
        v-for="task in taskStore.favs"
        class="mt-5 flex items-center justify-between rounded bg-white p-5 shadow-md"
      >
        <TaskDetails :task="task" />
      </li>
    </ul>
  </main>
</template>

<script setup>
import { ref } from "vue";
import TaskDetails from "./components/TaskDetails.vue";
import { useTaskStore } from "./stores/TaskStore";
import TaskForm from "./components/TaskForm.vue";

const taskStore = useTaskStore();

const filter = ref("all");
</script>
