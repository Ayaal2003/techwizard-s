<template>
  <div class="task-buttons">
    <!-- Кнопки с заданиями -->
    <button
      v-for="(task, index) in tasks"
      :key="index"
      @click="openModal(index)"
    >
      Задание {{ index + 1 }}
    </button>

    <!-- Модальное окно с анимацией -->
    <transition name="modal">
      <div v-if="isModalOpen" class="modal" @click.self="closeModal">
        <div class="modal-content">
          <!-- Кнопка закрытия -->
          <span class="close" @click="closeModal">&times;</span>

          <!-- Заголовок -->
          <h2>Задание {{ currentTaskIndex + 1 }}</h2>

          <!-- Описание задания -->
          <p>{{ tasks[currentTaskIndex].description }}</p>
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isModalOpen: false, // Состояние модального окна
      currentTaskIndex: 0, // Индекс текущего задания
      tasks: [
        {
          description: "Описание задания 1: Сделать что-то важное.",
        },
        {
          description: "Описание задания 2: Проверить отчеты.",
        },
        {
          description: "Описание задания 3: Подготовить презентацию.",
        },
        {
          description: "Описание задания 4: Отправить письмо клиенту.",
        },
      ],
    };
  },
  methods: {
    // Открыть модальное окно
    openModal(index) {
      this.currentTaskIndex = index;
      this.isModalOpen = true;
    },
    // Закрыть модальное окно
    closeModal() {
      this.isModalOpen = false;
    },
  },
};
</script>

<style scoped>
/* Стили для кнопок */
.task-buttons {
  display: flex;
  gap: 10px;
  justify-content: center;
  margin-top: 20px;
}

button {
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
  border: none;
  border-radius: 5px;
  background-color: #007bff;
  color: white;
}

button:hover {
  background-color: #0056b3;
}

/* Стили для модального окна */
.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal-content {
  background-color: #fff;
  padding: 20px;
  border-radius: 10px;
  width: 400px;
  text-align: center;
  position: relative;
}

.close {
  font-size: 24px;
  cursor: pointer;
  position: absolute;
  top: 10px;
  right: 10px;
}

.close:hover {
  color: #000;
}

/* Анимация для модального окна */
.modal-enter-active,
.modal-leave-active {
  transition: opacity 0.3s ease;
}

.modal-enter-from,
.modal-leave-to {
  opacity: 0;
}

.modal-enter-to,
.modal-leave-from {
  opacity: 1;
}

/* Анимация для содержимого модального окна */
.modal-content {
  animation: scaleUp 0.3s ease;
}

@keyframes scaleUp {
  from {
    transform: scale(0.9);
    opacity: 0;
  }
  to {
    transform: scale(1);
    opacity: 1;
  }
}
</style>
