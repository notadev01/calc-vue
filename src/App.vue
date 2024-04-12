<script setup>
import Cabecalho from './components/Cabecalho.vue';
import Calculadora from './components/Calculadora.vue';
import { reactive } from 'vue';

  const estado = reactive({
    valor1: 0,
    valor2: 0,
    operacao: 'somar',
    resultado: 0,
  })

  const trocarOperacao = (e) => {
    estado.operacao = e.target.value
    getResultado()
  }

  const getResultado = () => {
    switch(estado.operacao) {
      case 'somar':
        estado.resultado = estado.valor1 + estado.valor2;
        break;
      case 'subtrair':
        estado.resultado = estado.valor1 - estado.valor2;
        break;
      case 'multiplicar':
        estado.resultado = estado.valor1 * estado.valor2;
        break;
      case 'dividir':
        estado.resultado = estado.valor1 / estado.valor2;
        break;
    }
  }
</script>

<template>
  <div class="container">
    <Cabecalho />
    <Calculadora :getResultado="getResultado" :trocarOperacao="trocarOperacao" :estado="estado"/>
  </div>
</template>