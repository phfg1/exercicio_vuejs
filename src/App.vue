<script setup>
import { reactive, computed } from 'vue';

const estado = reactive({
  numA: 0,
  numB: 0,
  operacao: 'soma',
});

const resultado = computed(() => {
  const numeroA = parseFloat(estado.numA) || 0;
  const numeroB = parseFloat(estado.numB) || 0;

  switch (estado.operacao) {
    case 'soma':
      return numeroA + numeroB;
    case 'subtrair':
      return numeroA - numeroB;
    case 'multiplicar':
      return numeroA * numeroB;
    case 'dividir':
      return numeroB !== 0 ? numeroA / numeroB : 'Erro: o divisor deve ser diferente de zero';
    default:
      return 0;
  }
});
</script>

<template>
  <div class="container">
    <header class="p-5 mb-4 mt-4 bg-secondary rounded-3">
      <h1 class="fw-bold text-center">Calculadora aritmética</h1>
      <div class="row">
        <div class="col-6">
          <p class="mt-4">
            <input type="number" required placeholder="Digite um número" v-model.number="estado.numA">
            <input type="number" required placeholder="Digite outro número" v-model.number="estado.numB">
          </p>
          <p class="text-start mt-3"><b>Resultado:</b> {{ resultado }} </p>
        </div>
        <div class="col-6">
          <p class="text-end mt-4">
            <span class="fw-bold me-2">Selecione a operação desejada:</span>
            <select v-model="estado.operacao">
              <option value="soma">Somar +</option>
              <option value="subtrair">Subtrair -</option>
              <option value="multiplicar">Multiplicar *</option>
              <option value="dividir">Dividir /</option>
            </select>
          </p>          
        </div>
      </div>
    </header>
  </div>
</template>