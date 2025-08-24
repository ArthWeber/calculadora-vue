<script setup>
import { ref, computed } from "vue";
import Cabecalho from "./components/Cabecalho.vue";
import Operacao from "./components/Operacao.vue";
import Resultado from "./components/Resultado.vue";

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
      return num2.value !== 0
        ? (num1.value / num2.value).toFixed(2)
        : "Erro (divisão por 0)";
    default:
      return 0;
  }
});
</script>

<template>
  <div class="container mt-5">
    <Cabecalho />

    <div class="card shadow p-4">
      <Operacao v-model:num1="num1" v-model:num2="num2" v-model:operacao="operacao" />

      <Resultado :resultado="resultado" />
    </div>
  </div>
</template>

<style scoped>
.card {
  border-radius: 1rem;
  background: #f9fafc;
}

input {
  font-size: 1.5rem;
}

select {
  cursor: pointer;
}
</style>