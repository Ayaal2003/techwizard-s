<template>
  <div class="shop-page">
    <h1>Магазин</h1>
    <div class="shop-items">
      <div class="shop-item">
        <h2>Telegram Pro</h2>
        <p>Подписка на Telegram Pro за 100 баллов</p>
        <button @click="buyTelegramPro">Купить за 100 баллов</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      userBalance: 500, // Пример баланса пользователя
    };
  },
  methods: {
    buyTelegramPro() {
      if (this.userBalance >= 100) {
        this.userBalance -= 100; // Списание баллов
        alert("Поздравляем! Вы приобрели подписку на Telegram Pro.");
        // Здесь можно добавить логику для активации подписки
      } else {
        alert("Недостаточно баллов для покупки.");
      }
    },
  },
};
</script>

<style scoped>
.shop-page {
  padding: 20px;
}

.shop-items {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.shop-item {
  border: 1px solid #ccc;
  border-radius: 8px;
  padding: 20px;
  background-color: #f9f9f9;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

.shop-item h2 {
  margin: 0 0 10px 0;
}

.shop-item p {
  margin: 0 0 20px 0;
}

.shop-item button {
  background-color: #007bff;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
}

.shop-item button:hover {
  background-color: #0056b3;
}
</style>
