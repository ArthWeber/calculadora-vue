<script setup>

import { ref, computed } from "vue";

const num1 = ref(0);
const num2 = ref(0);
const operacao = ref("soma");

const resultado = computed(() => {
  switch (operacao.value) {
    case "soma":
      return num1.value + num2.value;
    case "subtracao":
      return num1.value - num2.value;
    case "multiplicacao":
      return num1.value * num2.value;
    case "divisao":
      return num2.value !== 0 ? (num1.value / num2.value).toFixed(2) : "Erro (divisão por 0)";
    default:
      return 0;
  }
});

</script>

<template>
  <div class="container mt-5">
    <header>
      <h1 class="text-center mb-3 p-3 bg-dark text-white rounded-3">Calculadora Aritmética</h1>
      <p class="text-center text-muted">Digite os valores que deseja calcular e selecione a operação desejada.</p>
    </header>
    <div class="card shadow p-4">
      <div class="row align-items-center g-3 text-center">
        <!-- Primeiro valor -->
        <div class="col-5">
          <input type="number" class="form-control" v-model.number="num1" placeholder="Primeiro valor" />
        </div>

        <!-- Operação -->
        <div class="col-2 d-flex justify-content-center">
          <select class="form-select text-center w-50" v-model="operacao">
            <option value="soma">+</option>
            <option value="subtracao">-</option>
            <option value="multiplicacao">x</option>
            <option value="divisao">÷</option>
          </select>
        </div>

        <!-- Segundo valor -->
        <div class="col-5">
          <input type="number" class="form-control" v-model.number="num2" placeholder="Segundo valor" />
        </div>
      </div>
      <!-- Resultado -->
      <div class="mt-4 text-center">
        <h4 class="fw-bold text-primary">Resultado: {{ resultado }}</h4>
      </div>
    </div>
  </div>

</template>

<style scoped>
.card {
  border-radius: 1rem;
}
</style>
