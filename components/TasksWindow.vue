<template>
  <div class="окно-заданий">
    <div class="значок-задания">
      <!-- Отображение баллов через data -->
      <span>Баллы: {{ points }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "TasksWindow",
  data() {
    return {
      points: 120, // Установка начального значения баллов
    };
  },
};
</script>

<style scoped>
.окно-заданий {
  position: absolute;
  top: 160px;
  right: 4px;
  z-index: 1000;
}

.значок-задания {
  background-color: #1c1c1d;
  color: white;
  padding: 14px 152px;
  border-radius: 0px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 13px;
  border: 1px solid #111111;
}

.значок-задания span {
  font-weight: bold;
}
</style>
