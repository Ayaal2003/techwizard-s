<script setup lang="ts">
import TasksWindow from "@/components/TasksWindow.vue";
import EmployeeCard from "@/components/EmployeeCard.vue";
import TaskButtons from "@/components/TaskButtons.vue";
import Tabs from "@/components/Tabs.vue";
import "@/assets/style.css";
import Name from "~/components/Name.vue";
import Number from "~/components/Number.vue";
import Nastroi from "~/components/Nastroi.vue";
import Rang from "~/components/Rang.vue";
import nik from "~/components/nik.vue";
</script>

<template>
  <div>
    <!-- Контент в зависимости от текущей вкладки -->
    <div v-if="currentTab === 'home'" class="profile-image-container">
      <TasksWindow />
      <EmployeeCard />
      <Name />
      <Number />
      <Nastroi />
      <Rang />
      <nik />
      <img src="/images/Employer.jpg" alt="Профиль" class="profile-image" />
      <img src="/images/Shkala.png" alt="Шкала" class="shkala-image" />
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

<
