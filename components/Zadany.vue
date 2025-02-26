<template>
  <div class="tasks-window">
    <div class="tasks-icon" @click="toggleCard">
      <span>Баллы: 120</span>
    </div>
    <div :class="['tasks-card', { open: isOpen }]">
      <!-- Плашки сверху -->
      <div class="card-header">
        <div class="header-plate header-plate-1">Работа</div>
        <div class="header-divider"></div>
        <!-- Разделитель -->
        <div class="header-plate header-plate-2">Баллы</div>
      </div>
      <!-- Список заданий -->
      <div class="tasks-list">
        <div v-for="(task, index) in tasks" :key="index" class="task-item">
          <span>{{ task.name }}</span>
          <span>{{ task.points }}</span>
        </div>
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
        { name: "Помощь коллегам", points: 50 },
        { name: "Квизы", points: 30 },
        { name: "Сверхурочная работа", points: 20 },
        { name: "Работа в выходные", points: 20 },
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
.tasks-window {
  position: fixed;
  top: 5px;
  right: 5px;
  z-index: 1000;
}

.tasks-icon {
  background-color: #007bff;
  color: white;
  padding: 10px 20px;
  border-radius: 20px;
  cursor: pointer;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 12px;
}

.tasks-icon span {
  font-weight: bold;
}

.tasks-card {
  background-color: white;
  border: 1px solid #ccc;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  max-height: 80vh;
  overflow-y: auto;
  transition: opacity 0.3s ease-out, transform 0.3s ease-out;
  opacity: 0;
  position: fixed;
  top: 170px;
  left: 306px;
  transform: translate(-50%, -50%) scale(0.9);
  z-index: 1001;
  width: 30%;
  max-width: 100%;
  box-sizing: border-box;
  font-size: 10px;
}

.tasks-card.open {
  opacity: 1;
  transform: translate(-50%, -50%) scale(1);
}

.card-header {
  display: flex;
  justify-content: space-between;
  gap: 10px;
  padding: 10px 10px;
  background-color: #ffffff;
  border-bottom: 1px solid #ffffff;
  position: sticky;
  top: 0;
  z-index: 1;
}

.header-plate {
  padding: 10px;
  border-radius: 5px;
  text-align: left;
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: left;
}

.header-plate-1 {
  background-color: #ffffff;
  color: rgb(0, 0, 0);
}

.header-plate-2 {
  background-color: #ffffff;
  color: rgb(0, 0, 0);
}

.header-divider {
  width: 1px;
  background-color: #ccc;
  margin: -20%;
}

.tasks-list {
  padding: 1px 1px 0; /* Отступы сверху и по бокам */
  overflow-y: auto;
  max-height: calc(80vh - 80px); /* Учитываем высоту плашек */
}

.task-item {
  display: flex;
  justify-content: space-between;
  padding: 4px 0; /* Отступы сверху и снизу */
  border-bottom: 1px solid #eee;
  font-size: 10px;
}

.task-item:last-child {
  border-bottom: none;
}

@media (max-width: 600px) {
  .tasks-card {
    padding: 10px;
  }
}
</style>
