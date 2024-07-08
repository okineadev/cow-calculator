<template>
  <div class="currency-converter">
    <div class="container">
      <h2><img src="../img/cow.png" alt="Cow" width="50">Cow calculator</h2>
      <div class="input-container">
        <label for="amount">Кількість:</label>
        <input type="text" id="amount" v-model="amount" />
      </div>
      <div class="input-container">
        <label for="currency">Виберіть валюту:</label>
        <select id="currency" v-model="selectedCurrency">
          <option value="cow">Корова</option>
          <option value="iphone">Iphone 15</option>
          <!-- Додайте інші валюти за потреби -->
        </select>
      </div>
      <div class="result">
        <p>{{ amount }} {{ selectedCurrency }} коштує {{ convertedAmount }} грн</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      amount: 0,
      selectedCurrency: 'cow', // Валюта за замовчуванням
    };
  },
  computed: {
    convertedAmount() {
      return this.amount * this.getExchangeRate(this.selectedCurrency);
    },
  },
  methods: {
    getExchangeRate(currency) {
      const table = {
        cow: 30_000,
        iphone: 40_000
      }

      return table[currency]
    },
  },
};
</script>

<style scoped>
h1, h2, h3, p, label {
  color: black;
}
.currency-converter {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
}

.container {
  width: 400px; /* фіксована ширина */
  height: 300px; /* фіксована висота */
  background-color: #fff; /* білий колір фону */
  padding: 20px;
  border-radius: 15px; /* заокруглені краї */
  box-shadow: 0 0 40px #000000cb;
  text-align: center;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
}

.input-container {
  margin-bottom: 15px;
}

label {
  display: block;
  margin-bottom: 5px;
}

input,
select {
  width: 100%;
  padding: 8px;
  box-sizing: border-box;
  border: 1px solid #ccc;
  border-radius: 4px;
  margin-top: 5px;
}

.result {
  margin-top: 20px;
}

h2 {
  margin-bottom: 10px;
  margin-top: 0;
  font-size: 30px;
  display: flex;
  justify-content: center;
  align-items: flex-end;
}

input, select {
  border-radius: 8px;
}

p {
  font-weight: bold;
  color: #333; /* темний текст */
}

img {
  margin-right: 10px;
}
</style>