<script setup lang="ts">
import IconPen from "@/components/icons/iconPen.vue";
import IconTrash from "@/components/icons/iconTrash.vue";
interface IListItems {
  id: number;
  text: string;
  done: boolean;
}
interface IListProps {
  tasks: IListItems[];
}

// props
defineProps<IListProps>();

//  emits
const emit = defineEmits<{
  (e: "taskDone", id: number): void;
}>();

// functions
function isComplated(id: number) {
  emit("taskDone", id);
}
</script>
<template>
  <div class="bg-[#FFFFFF] md:p-4 p-3">
    <ul>
      <li
        v-for="task in tasks"
        :key="task.id"
        class="cursor-pointer px-2.5 py-2 border rounded-lg mb-2 md:mb-4 flex justify-between items-center"
      >
        <div
          class="flex items-center gap-2"
          :class="task.done ? 'line-through' : ''"
          @click="isComplated(task.id)"
        >
          <input type="checkbox" v-model="task.done" />
          <span :for="task.id"> {{ task.text }}</span>
        </div>
        <div class="flex items-center gap-2 md:gap-4">
          <button type="button">
            <IconPen />
          </button>
          <button type="button">
            <IconTrash />
          </button>
        </div>
      </li>
    </ul>
  </div>
</template>
