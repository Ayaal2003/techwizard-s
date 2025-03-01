<template>
  <div class="окно-заданий">
    <!-- Кнопка для открытия модального окна -->
    <div class="значок-заданий" @click="openModal">
      <span>Таблицы лидеров</span>
    </div>

    <!-- Модальное окно с анимацией -->
    <transition name="modal">
      <div v-if="showModal" class="modal-overlay" @click.self="closeModal">
        <div class="modal-content">
          <!-- Кнопка закрытия -->
          <span class="close" @click="closeModal">&times;</span>
          <h2>Рейтинг сотрудников компании</h2>

          <!-- Список сотрудников с рангами -->
          <ul>
            <li v-for="(employee, index) in employees" :key="index">
              <strong>{{ index + 1 }}. {{ employee.name }}</strong> —
              {{ employee.points }} баллов
            </li>
          </ul>
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  name: "Rang",
  data() {
    return {
      showModal: false,
      // Пример данных сотрудников (можно заменить на реальные данные с сервера)
      employees: [
        { name: "Дмитрий Осипов", points: 250 },
        { name: "Анна Смирнова", points: 220 },
        { name: "Петр Петров", points: 200 },
        { name: "Мария Кузнецова", points: 180 },
        { name: "Алексей Сидоров", points: 150 },
      ],
    };
  },
  methods: {
    openModal() {
      this.showModal = true;
    },
    closeModal() {
      this.showModal = false;
    },
  },
};
</script>

<style scoped>
/* Кнопка "Таблицы лидеров" */
.окно-заданий {
  position: absolute;
  top: 248px;
  right: -6px;
  z-index: 1000;
}

.значок-заданий {
  background-color: #1c1c1d;
  color: white;
  padding: 14px 170px;
  border-radius: 0px;
  cursor: pointer;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 13px;
  border: 1px solid #111111;
}

.значок-заданий span {
  font-weight: bold;
}

/* Модальное окно */
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 2000;
}

.modal-content {
  background-color: white;
  padding: 30px;
  border-radius: 10px;
  max-width: 500px;
  width: 90%;
  position: relative;
  text-align: center;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
}

/* Кнопка закрытия */
.close {
  position: absolute;
  top: 10px;
  right: 15px;
  font-size: 24px;
  color: #333;
  cursor: pointer;
}

/* Анимация открытия/закрытия */
.modal-enter-active,
.modal-leave-active {
  transition: opacity 0.3s, transform 0.3s;
}

.modal-enter-from,
.modal-leave-to {
  opacity: 0;
  transform: scale(0.8);
}

ul {
  list-style: none;
  padding: 0;
  margin-top: 20px;
}

li {
  margin: 10px 0;
  font-size: 16px;
}
</style>
