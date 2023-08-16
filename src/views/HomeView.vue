<script setup lang="ts">
import { ref } from "vue";

const tasks = ref([
  { id: 1, text: "nimadir", done: true },
  { id: 2, text: "nimadir", done: false },
  { id: 3, text: "nimadir", done: false },
  { id: 4, text: "nimadir", done: true },
  { id: 5, text: "nimadir", done: false },
]);

// functions
function taskDone(id: number) {
  tasks.value.map((item) => {
    if (item.id === id) {
      item.done = !item.done;
    }
  });
}
</script>
<template>
  <main class="h-screen px-3 md:px-6 bg-[rgb(60,139,117)]">
    <section class="max-w-3xl mx-auto py-10">
      <div
        class="bg-[#F2F2F2] text-white flex md:gap-0 gap-1 items-center justify-center md:justify-between flex-wrap md:p-4 p-2"
      >
        <h1 class="text-[#447FBD] font-bold text-2xl">TodoApp</h1>
        <div class="block md:flex justify-end gap-4 items-center">
          <button
            type="button"
            class="md:w-auto w-full bg-[#447FBD] border rounded-lg p-1.5"
          >
            All
            <span class="bg-white text-[#447FBD] rounded-full px-1">
              {{ tasks.length }}
            </span>
          </button>
          <button
            type="button"
            class="md:w-auto w-full bg-[#447FBD] border rounded-lg p-1.5"
            @click="isCompleted"
          >
            Complated
            <span class="bg-white text-[#447FBD] rounded-full px-1">
              {{ tasks.length }}
            </span>
          </button>
          <button
            type="button"
            class="md:w-auto w-full bg-[#447FBD] border rounded-lg p-1.5"
          >
            Not complated
            <span class="bg-white text-[#447FBD] rounded-full px-1">
              {{ tasks.length }}
            </span>
          </button>
        </div>
      </div>
      <div class="bg-[#FFFFFF] md:p-4 p-3">
        <ul>
          <li
            v-for="task in tasks"
            :key="task.id"
            class="cursor-pointer px-2.5 py-2 border rounded-lg mb-2 md:mb-4 flex justify-between items-center"
            @click="taskDone(task.id)"
          >
            <span :class="task.done ? 'line-through' : ''">{{
              task.text
            }}</span>
            <div class="flex items-center gap-2 md:gap-4">
              <button type="button">edit</button>
              <button type="button">delete</button>
            </div>
          </li>
        </ul>
      </div>
    </section>
  </main>
</template>
