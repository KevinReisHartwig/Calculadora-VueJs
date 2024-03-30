<script setup>
import { reactive } from 'vue';

const estado = reactive({
  numero1: '',
  numero2: '',
  operacao: '+',
  resultado: 0
});

const calcular = () => {
  const num1 = parseFloat(estado.numero1);
  const num2 = parseFloat(estado.numero2);

  switch (estado.operacao) {
    case '+':
      estado.resultado = num1 + num2;
      return estado.resultado;
    case '-':
      estado.resultado = num1 - num2;
      return estado.resultado;
    case '*':
      estado.resultado = num1 * num2;
      return estado.resultado;
    case '/':
      estado.resultado = num1 / num2;
      return estado.resultado;
  }
};
</script>

<template>
  <div class="container">
    <header class="p-5 mb-4 mt-5 bg-light rounded-3">
      <h1>Calculadora Aritmética</h1>
    </header>
    <div class="row">
      <div class="col-md-4">
        <input type="number" v-model="estado.numero1" @input="calcular" class="form-control mb-3"
          placeholder="Digite o primeiro número">
      </div>
      <div class="col-md-4">
        <select v-model="estado.operacao" @input="calcular" class="form-select mb-3">
          <option value="+">+</option>
          <option value="-">-</option>
          <option value="*">*</option>
          <option value="/">/</option>
        </select>
      </div>
      <div class="col-md-4">
        <input type="number" v-model="estado.numero2" @input="calcular" class="form-control mb-3"
          placeholder="Digite o segundo número">
      </div>
      <div class="col">
        <h4>Resultado: {{ estado.resultado }}</h4>
      </div>
    </div>
  </div>
</template>
