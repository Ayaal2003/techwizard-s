<template>
  <div class="tasks-window">
    <div class="tasks-icon">
      <span>Настройки</span>
    </div>
  </div>
</template>

<style scoped>
.tasks-window {
  position: absolute;
  top: 204px;
  right: -2px;
  z-index: 1000;
}

.tasks-icon {
  background-color: #1c1c1d;
  color: white;
  padding: 14px 158px;
  border-radius: 0px;
  cursor: pointer;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 13px;
  border: 1px solid #111111;
}

.tasks-icon span {
  font-weight: bold;
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
