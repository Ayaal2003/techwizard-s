<template>
  <div class="tasks-card">
    <div class="tasks-header" @click="toggleCard">
      <h2>Задания</h2>
      <span>{{ isOpen ? "▲" : "▼" }}</span>
    </div>
    <div v-if="isOpen" class="tasks-content">
      <div v-for="(task, index) in tasks" :key="index" class="task-item">
        <span>{{ task.name }}</span>
        <span>{{ task.points }} баллов</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isOpen: false,
      tasks: [
        { name: "Задание 1: Пройти обучение", points: 50 },
        { name: "Задание 2: Заполнить профиль", points: 30 },
        { name: "Задание 3: Пригласить друга", points: 20 },
      ],
    };
  },
  methods: {
    toggleCard() {
      this.isOpen = !this.isOpen;
    },
  },
};
</script>

<style scoped>
.tasks-card {
  border: 1px solid #ccc;
  border-radius: 8px;
  margin: 10px;
  padding: 10px;
  background-color: #f9f9f9;
}

.tasks-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  cursor: pointer;
}

.tasks-header h2 {
  margin: 0;
}

.tasks-content {
  margin-top: 10px;
}

.task-item {
  display: flex;
  justify-content: space-between;
  padding: 8px;
  border-bottom: 1px solid #eee;
}

.task-item:last-child {
  border-bottom: none;
}
</style>
