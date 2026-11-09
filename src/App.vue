<script setup>

import { ref, computed } from 'vue'

const numeroA = ref('')
const numeroB = ref('')
const operacao = ref('+')

const resultado = computed(() => {
  if (numeroA.value === '' || numeroB.value === '') {
    return ''
  }

  switch (operacao.value) {
    case '+':
      return numeroA.value + numeroB.value
    case '-':
      return numeroA.value - numeroB.value
    case '*':
      return numeroA.value * numeroB.value
    case '/':
      if (numeroB.value === 0) {
        return 'Divisão por zero'
      } 
      return numeroA.value / numeroA.value
  }
})
</script>
<template>
  
  <div class="container-box">
    <h1 class="title">Calculadora Aritmética </h1>
    <hr>
    <div class="calculadora-container">
      <input v-model.number="numeroA" type="number" placeholder="Digite um valor válido">
      <input v-model.number="numeroB" type="number" placeholder="Digite um valor válido">
      <select v-model="operacao">
        <option value="+">+</option>
        <option value="-">-</option>
        <option value="/">/</option>
        <option value="*">x</option>
      </select>
      <h2>:{{resultado}}</h2>
    </div>
  </div>

</template>

<style scoped>

.container-box {
  font-family: 'Courier New', Courier, monospace;
  display: flex;
  flex-direction: column;
  align-items: center;
  max-width: 60vh;
  border: 1px solid black;
  border-radius: 2vh;
  margin: auto;
}

hr {
  margin: 0 0 2vh 0;
  width: 90%;
}

.calculadora-container {
  align-items: center;
  display: flex;
  flex-direction: row;
  gap: 1vh;

  input {
    height: 26px;
    width: 10vh;
    margin-bottom: 2vh;
  }

  select {
    height: 33px;
    width: 5vh;
    margin-bottom: 2vh;
  }

  h2 {
    margin: 0;
    margin-bottom: 2vh;
  }
}

</style>
