<template>
  <div class="task-window">
    <div class="task-icon">
      <span>@Serber</span>
    </div>
  </div>
</template>

<style scoped>
.task-window {
  position: absolute;
  top: 54px;
  right: 168px;
  z-index: 1000;
}

.task-icon {
  padding: 15px 20px;
  border-radius: 20px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 12px;
}

.task-icon span {
  font-weight: bold;
  color: #7e7e82;
}

@media (max-width: 600px) {
  .tasks-card {
    padding: 10px;
  }
}
</style>
