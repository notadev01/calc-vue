<script setup>
    const props = defineProps(['getResultado', 'trocarOperacao', 'estado'])
</script>

<template>
    <div class="row">
        <div class="col-md-3"></div>
        <div class="col-md-2">
            <input @input="props.getResultado" v-model="props.estado.valor1" required type="number" placeholder="Valor 1"
                class="form-control">
        </div>
        <div class="col-md-2">
            <select @change="props.trocarOperacao" v-model="props.estado.operacao" class="form-control">
                <option value="somar">Somar</option>
                <option value="subtrair">Subtrair</option>
                <option value="multiplicar">Multiplicar</option>
                <option value="dividir">Dividir</option>
            </select>
        </div>
        <div class="col-md-2">
            <input @input="props.getResultado" v-model="props.estado.valor2" required type="number" placeholder="Valor 2"
                class="form-control">
        </div>
        <br>
        <h2 class="text-center mt-5">{{ props.estado.resultado }}</h2>
        <div class="col-md-3"></div>
    </div>
</template>