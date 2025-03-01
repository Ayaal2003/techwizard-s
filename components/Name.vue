<template>
  <div class="task-window">
    <span>Иванов Иван</span>
  </div>
</template>

<style scoped>
.task-window {
  position: absolute;
  top: 12px;
  right: 123px;
  z-index: 1000;
  padding: 10px 20px;
  border-radius: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 15px;
  font-weight: bold;
  color: #ffffff;
}

/* 📱 Адаптация под мобильные устройства */
@media (max-width: 768px) {
  .task-window {
    top: 10px;
    left: 240px;
    padding: 8px 15px;
    font-size: 14px;
    border-radius: 15px;
  }
}

@media (max-width: 480px) {
  .task-window {
    top: 8px;
    left: 130px;
    padding: 6px 10px;
    font-size: 12px;
    border-radius: 10px;
    max-width: 80%; /* Ограничение по ширине на маленьких экранах */
    overflow-wrap: break-word; /* Перенос длинного текста */
  }
}
</style>
