<script setup>
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
    <header class="p-5 mb-4 mt-4 bg-secondary rounded-3">
        <h1 class="text-center">Calculadora aritmética</h1>
    </header>

    <div class="row">
      <div class="col-md-3"></div>
      <div class="col-md-2">
          <input @input="getResultado()" v-model="estado.valor1" required type="number" placeholder="Valor 1" class="form-control">
      </div>
      <div class="col-md-2">
          <select @change="trocarOperacao" v-model="estado.operacao" class="form-control">
              <option value="somar">Somar</option>
              <option value="subtrair">Subtrair</option>
              <option value="multiplicar">Multiplicar</option>
              <option value="dividir">Dividir</option>
          </select>
      </div>
      <div class="col-md-2">
          <input @input="getResultado()" v-model="estado.valor2" required type="number" placeholder="Valor 2" class="form-control">
      </div>
      <br>
      <h2 class="text-center mt-5">{{ estado.resultado }}</h2>
      <div class="col-md-3"></div>
    </div>
  </div>
</template>