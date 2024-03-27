<template>
  <div class="calculator">
    <input type="number" v-model.number="num1" @input="calculate">
    <select v-model="operator" @change="calculate">
      <option value="add">+</option>
      <option value="subtract">-</option>
      <option value="multiply">*</option>
      <option value="divide">/</option>
    </select>
    <input type="number" v-model.number="num2" @input="calculate">
    <div class="result">Resultado: {{ result }}</div>
  </div>
</template>

<script setup>
  import { ref } from 'vue';

  const num1 = ref(0);
  const num2 = ref(0);
  const operator = ref('add');
  const result = ref(0);

  const calculate = () => {
    switch (operator.value) {
      case 'add':
        result.value = num1.value + num2.value;
        break;
      case 'subtract':
        result.value = num1.value - num2.value;
        break;
      case 'multiply':
        result.value = num1.value * num2.value;
        break;
      case 'divide':
        result.value = num2.value !== 0 ? num1.value / num2.value : 'Erro: Divisão por zero';
        break;
      default:
        result.value = 0;
    }
  };
</script>

<style scoped>
.calculator {
  max-width: 300px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 8px;
  background-color: #f5f5f5;
  display: flex;
  flex-direction: column;
  align-items: center;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

input[type="number"], select {
  margin: 10px;
  padding: 8px;
  font-size: 16px;
  border-radius: 4px;
  border: 1px solid #ccc;
}

.result {
  margin-top: 20px;
  font-size: 18px;
  color: #333;
}
</style>