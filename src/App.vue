<script setup>

import { ref, watch } from 'vue';

const selected = ref('');
const valor1 = ref(0);
const valor2 = ref(0);
const resultado = ref(0);

function Soma(a, b) {
  return a + b;
}

function Subtracao(a, b) {
  return a - b;
}

function Divisao(a, b) {
  return a / b;
}

function Multiplicacao(a, b) {
  return a * b;
}

watch([valor1, valor2, selected], () => {
  calcular();
});


function calcular() {
  if (selected.value === '+') {
    resultado.value = Soma(valor1.value, valor2.value);
  } else if (selected.value === '-') {
    resultado.value = Subtracao(valor1.value, valor2.value);
  } else if (selected.value === '/') {
    resultado.value = Divisao(valor1.value, valor2.value);
  } else if (selected.value === '*') {
    resultado.value = Multiplicacao(valor1.value, valor2.value);
  }
}
</script>

<template>
  <div id="app" class="p-4">
    <h1>Primeira Calculadora Vue</h1>
    <h4>Insira os números que deseja calcular e selecione a operação</h4>
    <br>
    <form id="app">
      <div class="row container">
        <input v-model="valor1" type="number" placeholder="Digite o primeiro valor" class="form-control">
        <input v-model="valor2" type="number" placeholder="Digite o segundo valor" class="form-control">
          <div class="selecao">
            <select v-model="selected" class="form-control">
            <option value="+" selected>+</option>
            <option value="-">-</option>
            <option value="*">*</option>
            <option value="/">/</option>
          </select>
          </div>
        <br>
        <span>Selecionado: {{ selected }}</span>
        <br>
        <output id="resultado" name="resultado">Resultado {{ resultado }}</output>
      </div>
    </form>
  </div>
</template>

<style scoped>
#app {
  background-color: #ced6e0;
  height: 100vh;
  text-align: center;
}

.container {
  max-width: 280px;
  display:inline-block;
}

input {
  margin-bottom: 10px;
  background-color: #f5e0b4;
}

option {
  text-align: center;
  font-size: 22px;
  font-weight: bold;
}

output {
  background-color: #2ed573;
  height: 50px;
  margin-top: 16px;
  font-size: 20px;
  font-weight: bold;
  border-radius: 4px;
  display: flex;
  align-items: center;
  justify-content: center;
}

</style>
