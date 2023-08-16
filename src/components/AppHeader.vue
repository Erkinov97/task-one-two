<script setup lang="ts">
import IconPlus from "@/components/icons/iconPlus.vue";

interface IHeaderProps {
  allTodos: number;
  complated: number;
  notComplated: number;
}

// props
withDefaults(defineProps<IHeaderProps>(), {
  allTodos: 5,
  complated: 5,
  notComplated: 5,
});

// emits
const emit = defineEmits<{
  (e: "addNewTodo"): void;
  (e: "showAll"): void;
  (e: "showComplated"): void;
  (e: "showNotComplated"): void;
}>();
</script>
<template>
  <div
    class="bg-[#F2F2F2] text-white flex md:gap-0 gap-1 items-center justify-center md:justify-between flex-wrap md:p-4 p-2"
  >
    <h1 class="text-[#447FBD] font-bold text-2xl">TodoApp</h1>
    <div class="block md:flex justify-end gap-4 items-center">
      <button
        type="button"
        class="md:w-auto w-full bg-[#447FBD] border rounded-lg p-1.5"
        @click="emit('showAll')"
      >
        All
        <span class="bg-white text-[#447FBD] rounded-full px-1">
          {{ allTodos }}
        </span>
      </button>
      <button
        type="button"
        class="md:w-auto w-full bg-[#447FBD] border rounded-lg p-1.5"
        @click="emit('showComplated')"
      >
        Complated
        <span class="bg-white text-[#447FBD] rounded-full px-1">
          {{ complated }}
        </span>
      </button>
      <button
        type="button"
        class="md:w-auto w-full bg-[#447FBD] border rounded-lg p-1.5"
        @click="emit('showNotComplated')"
      >
        Not complated
        <span class="bg-white text-[#447FBD] rounded-full px-1">
          {{ notComplated }}
        </span>
      </button>
      <button
        type="button"
        class="md:w-auto w-full bg-[#447FBD] border rounded-lg p-1.5 flex items-center gap-2 justify-center"
        @click="emit('addNewTodo')"
      >
        <IconPlus />
        <span>Add Todo</span>
      </button>
    </div>
  </div>
</template>
