<script setup>


new Vue({
  el: '...',
  data: {
    selected: '',
    options: [
      { text: 'Selecione', value: '' },
      { text: 'Adição', value: '+' },
      { text: 'Subtração', value: '-' },
      { text: 'Divisão', value: '/' },
      { text: 'Multiplicação', value: '*' }
    ]
  }
})



function Calculo(valor1, valor2, operacao) {
  var resultado = 0;

  if (operacao == "+")
      resultado = Soma(valor1, valor2);

  if (operacao == "-")
      resultado = subtração(valor1, valor2);

  if (operacao == "/")
  resultado = divisão(valor1, valor2);

  if (operacao == "*")
  resultado = multiplicação(valor1, valor2);
  
      return resultado;
}
</script>


<template>
  <div id="app" class="p-4">
    <h1>Primeira Calculadora Vue</h1>
    <h4>Insira os números que deseja calcular e selecione o operação</h4>
    <br>
    <form id="app" @submit="checkForm">
      <div class="row container">
      <input id="valor1" name="valor1" type="number" placeholder="Digite o primeiro valor" class="form-control">
      <input id="valor2" name="valor2" type="number" placeholder="Digite o segundo valor" class="form-control">
      <select v-model="selected" class="form-control">
        <option v-for="option in options" v-bind:value="option.value">
        {{ option.text }}
        </option>
      </select>
      <br>
      <span>Selecionado: {{ selected }}</span>
      <br>
      <output id="resultado" name="resultado">Resultado {{ Calculo() }}</output>
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
