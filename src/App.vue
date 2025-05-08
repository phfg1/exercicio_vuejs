<script setup>
import { reactive, computed } from 'vue';
import InputNumerico from './components/InputNumerico.vue';
import SeletorOperacao from './components/SeletorOperacao.vue';
import ResultadoCalculo from './components/ResultadoCalculo.vue';

const estado = reactive({
  numA: 0,
  numB: 0,
  operacao: 'soma',
});

const resultadoCalculado = computed(() => {
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
        <div class="col-6 d-flex">
          <InputNumerico 
            class="me-3"
            placeholder="Digite um número"
            v-model="estado.numA"
          />
          <InputNumerico
            placeholder="Digite outro número"
            v-model="estado.numB"
          />          
        </div>
        <div class="col-6">
          <SeletorOperacao v-model="estado.operacao" />
        </div>
      </div>
      <div class="row">
        <div class="col-12">
          <ResultadoCalculo :resultado="resultadoCalculado" />
        </div>
      </div>
    </header>
  </div>
</template>

<style scoped>
.container {
  max-width: 980px;
  margin: 0 auto;
}
</style>