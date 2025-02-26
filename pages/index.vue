<script setup lang="ts">
import TasksWindow from "@/components/TasksWindow.vue";
import EmployeeCard from "@/components/EmployeeCard.vue";
import TaskButtons from "@/components/TaskButtons.vue";
</script>

<template>
  <div>
    <!-- Контент в зависимости от текущей вкладки -->
    <div v-if="currentTab === 'home'">
      <TasksWindow />
      <EmployeeCard />
    </div>
    <div v-else-if="currentTab === 'zadanie'">
      <TaskButtons />
    </div>
    <div v-else-if="currentTab === 'magaz'">
      <h1>Потратить баллы</h1>
    </div>

    <!-- Компонент вкладок -->
    <Tabs :tabs="tabs" :initialTab="currentTab" @tab-change="changeTab" />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

interface User {
  name: string;
  score: number;
}

interface Tab {
  id: string;
  label: string;
}

export default defineComponent({
  data() {
    return {
      currentTab: "home" as string,
      score: 100 as number,
      topUsers: [
        { name: "Иван Иванов", score: 500 },
        { name: "Петр Петров", score: 450 },
        { name: "Сидор Сидоров", score: 400 },
      ] as User[],
      tabs: [
        { id: "home", label: "Главная" },
        { id: "zadanie", label: "Задание" },
        { id: "magaz", label: "Магазин" },
      ] as Tab[],
    };
  },
  methods: {
    changeTab(tab: string) {
      this.currentTab = tab;
    },
  },
});
</script>

<style scoped>
/* Стили для контента */
div {
  padding: 20px;
}
</style>
