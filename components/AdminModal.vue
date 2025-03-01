<template>
  <div class="modal-overlay" @click.self="closeModal">
    <div class="modal-content">
      <h2>Вход</h2>
      <input v-model="login" type="text" placeholder="Логин или почта" />
      <input v-model="password" type="password" placeholder="Пароль" />
      <button @click="submit">Войти</button>

      <p v-if="errorMessage" class="error">{{ errorMessage }}</p>

      <span class="close" @click="closeModal">&times;</span>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, defineEmits } from "vue";
import { useRouter } from "vue-router";

const emit = defineEmits(["close"]);
const router = useRouter();

// ✅ Создание реактивных переменных через ref()
const login = ref("");
const password = ref(""); // Здесь создается password, чтобы избежать ошибки ts(2304)
const errorMessage = ref("");

const submit = () => {
  if (login.value === "admin" && password.value === "admin") {
    router.push("/admin"); // Переход на страницу /admin
    emit("close"); // Закрыть модальное окно
  } else {
    errorMessage.value = "Неправильный логин или пароль";
  }
};

const closeModal = () => {
  emit("close");
  errorMessage.value = "";
  login.value = "";
  password.value = "";
};
</script>

<style scoped>
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
  z-index: 1000;
}

.modal-content {
  background-color: white;
  padding: 20px;
  border-radius: 10px;
  max-width: 400px;
  width: 90%;
  position: relative;
  text-align: center;
}

input {
  display: block;
  width: 100%;
  padding: 10px;
  margin: 10px 0;
  border: 1px solid #ddd;
  border-radius: 5px;
}

button {
  padding: 10px;
  width: 100%;
  border: none;
  background-color: #3498db;
  color: white;
  border-radius: 5px;
  cursor: pointer;
  margin-top: 10px;
}

.error {
  color: red;
  margin-top: 10px;
}

.close {
  position: absolute;
  top: 10px;
  right: 15px;
  font-size: 24px;
  cursor: pointer;
}
</style>
