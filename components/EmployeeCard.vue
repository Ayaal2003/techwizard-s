<template>
  <div class="tasks-window">
    <div class="tasks-icon">
      <span>Ранг: 5</span>
    </div>
  </div>
</template>

<style scoped>
.tasks-window {
  position: absolute;
  top: 122px;
  right: 262px;
  z-index: 1000;
}

.tasks-icon {
  background-color: #ffffff;
  color: rgb(0, 0, 0);
  padding: 4px 20px;
  border-radius: 20px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
  display: absolute;
  align-items: center;
  justify-content: center;
  font-size: 14px;
}

.tasks-icon span {
  font-weight: bold;
}

@media (max-width: 600px) {
  .tasks-card {
    padding: 10px;
  }
}
</style>
