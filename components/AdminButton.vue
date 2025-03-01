<template>
  <div class="admin-button" @click="openModal">Админ</div>

  <!-- Модальное окно авторизации с анимацией -->
  <transition name="modal-fade">
    <AdminModal v-if="showModal" @close="closeModal" />
  </transition>
</template>

<script setup lang="ts">
import { ref } from "vue";
import AdminModal from "@/components/AdminModal.vue";

const showModal = ref(false);

const openModal = () => {
  showModal.value = true;
};

const closeModal = () => {
  showModal.value = false;
};
</script>

<style scoped>
.admin-button {
  position: absolute;
  top: 10px;
  right: 10px;
  padding: 10px 20px;
  background-color: #3498db;
  color: white;
  border-radius: 5px;
  cursor: pointer;
  font-weight: bold;
  transition: background-color 0.3s;
}

.admin-button:hover {
  background-color: #2980b9;
}
</style>
