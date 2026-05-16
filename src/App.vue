<script setup>
import { reactive, computed } from "vue";

const estado = reactive({
  numero1: 0,
  numero2: 0,
  operacao: "soma",
});

const resultado = computed(() => {
  const { numero1, numero2, operacao } = estado;

  switch (operacao) {
    case "soma":
      return numero1 + numero2;
    case "subtracao":
      return Math.abs(numero1 - numero2);
    case "multiplicacao":
      return numero1 * numero2;
    case "divisao":
      return numero2 !== 0 ? numero1 / numero2 : "Erro (divisão por zero)";
    default:
      return 0;
  }
});
</script>

<template>
  <div class="container mt-5">
    <h1>🧮 Calculadora Aritmética</h1>

    <div class="row mt-4">
      <div class="col-md-4">
        <input
          type="number"
          v-model.number="estado.numero1"
          class="form-control"
          placeholder="Digite o primeiro número"
        />
      </div>

      <div class="col-md-4">
        <input
          type="number"
          v-model.number="estado.numero2"
          class="form-control"
          placeholder="Digite o segundo número"
        />
      </div>

      <div class="col-md-4">
        <select v-model="estado.operacao" class="form-select">
          <option value="soma">Soma (+)</option>
          <option value="subtracao">Subtração (-)</option>
          <option value="multiplicacao">Multiplicação (×)</option>
          <option value="divisao">Divisão (÷)</option>
        </select>
      </div>
    </div>

    <div class="mt-4">
      <h3>Resultado: {{ resultado }}</h3>
    </div>
  </div>
</template>

<style scoped>
.container {
  max-width: 700px;
  margin: auto;
  padding: 20px;
  border-radius: 12px;
  background: #f9f9f9;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
}

h1 {
  text-align: center;
  color: #0047ab; /* Azul Tekhelet */
}

h3 {
  text-align: center;
  color: #800080; /* Púrpura Argaman */
  font-weight: bold;
}
</style>
