<template>
  <div class="tasks-page">
    <!-- Кнопки заданий -->
    <div
      v-for="(task, index) in tasks"
      :key="index"
      :class="['task-button', task.customClass]"
      :style="task.customStyle"
      @click="openModal(task)"
    >
      {{ task.name }}
    </div>

    <!-- Модальное окно для заданий -->
    <transition name="modal" @after-leave="resetModal">
      <div v-if="activeTask" class="modal-overlay" @click.self="closeModal">
        <div class="modal-content">
          <span class="close" @click="closeModal">&times;</span>
          <h2>{{ activeTask.name }}</h2>
          <p>{{ activeTask.description }}</p>
          <p v-if="activeTask.name !== 'Квизы'">
            Баллы за выполнение: {{ activeTask.points }}
          </p>

          <!-- Специальный контент для квиза -->
          <div v-if="activeTask.name === 'Квизы'" class="quiz-content">
            <p>Вопрос: 2 + 2 = ?</p>
            <input
              v-model="quizAnswer"
              type="number"
              placeholder="Введите ответ"
            />
            <button @click="submitQuizAnswer">Ответить</button>
            <p>Баллы за правильный ответ: {{ activeTask.points }}</p>
          </div>
        </div>
      </div>
    </transition>

    <!-- Отображение текущих баллов -->
    <div class="tasks-window">
      <div class="tasks-icon">
        <span>Баллы: {{ totalPoints }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      activeTask: null,
      quizAnswer: "",
      totalPoints: 120, // Начальные баллы
      tasks: [
        {
          name: "Сверхурочная работа",
          description: "Выполнение задач в нерабочее время.",
          points: 20,
          customClass: "overtime-task",
          customStyle: { backgroundColor: "#FF5722", color: "#FFFFFF" },
        },
        {
          name: "Работа в выходные",
          description: "Работа в выходной день начисляет 30 баллов.",
          points: 30,
          customClass: "weekend-task",
          customStyle: { backgroundColor: "#3F51B5", color: "#FFFFFF" },
        },
        {
          name: "Помощь коллегам",
          description: "Помогайте коллегам и зарабатывайте баллы.",
          points: 50,
          customClass: "help-task",
          customStyle: { backgroundColor: "#4CAF50", color: "#FFFFFF" },
        },
        {
          name: "Квизы",
          description: "Пройдите квиз и получите до 40 баллов.",
          points: 40,
          customClass: "quiz-task",
          customStyle: { backgroundColor: "#9C27B0", color: "#FFFFFF" },
        },
      ],
    };
  },
  methods: {
    openModal(task) {
      this.activeTask = task;
    },
    closeModal() {
      this.activeTask = null;
      this.quizAnswer = "";
    },
    resetModal() {
      this.closeModal();
    },
    submitQuizAnswer() {
      if (parseInt(this.quizAnswer) === 4) {
        this.totalPoints += this.activeTask.points;
        alert(
          "Правильный ответ! Вам начислено " +
            this.activeTask.points +
            " баллов."
        );
        this.closeModal();
      } else {
        alert("Неправильный ответ. Попробуйте снова!");
      }
    },
  },
};
</script>
