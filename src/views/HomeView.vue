<script setup lang="ts">
import { ref } from "vue";
import AppHeader from "@/components/AppHeader.vue";
import AppList from "@/components/AppList.vue";

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
      <AppHeader :not-complated="0" :complated="1" :all-todos="tasks.length" />
      <AppList :tasks="tasks" @task-done="taskDone" />
    </section>
  </main>
</template>
