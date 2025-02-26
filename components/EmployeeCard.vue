<template>
  <div class="employee-card">
    <!-- Иконка работника -->
    <img :src="employee.icon" alt="Иконка работника" class="employee-icon" />

    <!-- Имя работника -->
    <div class="employee-name">{{ employee.name }}</div>

    <!-- Кнопка рейтинга -->
    <div class="employee-rating" @click="openRatingModal">
      Рейтинг: {{ employee.rating }} ★
    </div>

    <!-- Информация о руководителе -->
    <div class="employee-manager">Руководитель: {{ employee.manager }}</div>

    <!-- Дата регистрации -->
    <div class="employee-registration-date">
      Дата регистрации: {{ employee.registrationDate }}
    </div>

    <!-- Модальное окно с рейтингами -->
    <div
      v-if="isModalOpen"
      class="modal-overlay"
      @click.self="closeRatingModal"
    >
      <div class="modal-content">
        <!-- Кнопка закрытия -->
        <span class="close" @click="closeRatingModal">&times;</span>

        <!-- Заголовок -->
        <h2>Рейтинг сотрудников</h2>

        <!-- Список рейтингов -->
        <ul>
          <li v-for="(emp, index) in employees" :key="index">
            {{ emp.name }}: {{ emp.rating }} ★
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isModalOpen: false, // Состояние модального окна
      employee: {
        icon: "/images/employee-icon.png", // Путь к иконке
        name: "Иван Иванов",
        rating: 4.5,
        manager: "Петр Петров",
        registrationDate: "2023-01-15",
      },
      employees: [
        { name: "Иван Иванов", rating: 4.5 },
        { name: "Петр Петров", rating: 4.7 },
        { name: "Мария Сидорова", rating: 4.3 },
      ],
    };
  },
  methods: {
    // Открыть модальное окно
    openRatingModal() {
      this.isModalOpen = true;
    },
    // Закрыть модальное окно
    closeRatingModal() {
      this.isModalOpen = false;
    },
  },
};
</script>

<style scoped>
/* Стили для карточки сотрудника */
.employee-card {
  text-align: center;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 10px;
  width: 200px;
  margin: 0 auto;
  background-color: #f9f9f9;
}

.employee-icon {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  margin-bottom: 10px;
}

.employee-name {
  font-size: 18px;
  font-weight: bold;
  margin: 10px 0;
}

/* Стили для кнопки рейтинга */
.employee-rating {
  font-size: 16px;
  color: #007bff;
  cursor: pointer;
  margin: 10px 0;
  padding: 10px;
  border-radius: 5px;
  background-color: #e3f2fd;
  transition: all 0.3s ease;
  display: inline-block;
}

.employee-rating:hover {
  background-color: #bbdefb;
  transform: scale(1.05);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

.employee-rating:active {
  transform: scale(0.95);
  background-color: #90caf9;
}

/* Стили для модального окна */
.modal-overlay {
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
  width: 300px;
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

ul {
  list-style-type: none;
  padding: 0;
}

ul li {
  margin: 10px 0;
}
</style>
