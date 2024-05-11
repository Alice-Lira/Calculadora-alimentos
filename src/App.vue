<script setup>
import {ref} from 'vue';

const valorInput = ref("");
const valorInputDias = ref("");
const resultadoDias = ref("")
const valorSelect = ref("")
const resultado = ref("")

const opcoes = ref([
  {valor: 1.3, titulo: "Frango"},
  {valor: 0.33, titulo: "Arroz"},
  {valor: 0.5, titulo: "Feijão"},
  {valor: 1.25, titulo: "Carne bovina"},
  {valor: 1.01, titulo: "Carne suina"}
])
const pesquisar = () =>{
  const alimentoCru = valorInput.value * valorSelect.value
  const alimentoSemana = alimentoCru * valorInputDias.value
  resultado.value = alimentoSemana.toFixed(0)
  resultadoDias.value = valorInputDias.value 

  valorInput.value = ''
  valorInputDias.value = ''
  valorSelect.value = ''
};
</script>
<template>
  <div class="flex justify-center h-screen items-center bg-gray-200">
    <div class=" flex flex-col px-3 py-5 bg-white shadow-lg rounded-lg">

        <label class="text-sm mt-3 font-semibold">Quantidade alimento cozido:</label>
        <input type="number" v-model="valorInput" class="bg-gray-200 rounded-md focus:outline-none p-1 w-1/2 mt-1  focus:border-blue-500 border border-gray-300"/>
        <label class="text-sm mt-3 font-semibold">Dias:</label>
        <input type="number" v-model="valorInputDias" class="bg-gray-200 rounded-md focus:outline-none p-1 w-1/2 mt-1  focus:border-blue-500 border border-gray-300"/>

        <p class="text-sm mt-3 font-semibold">Selecione um alimento:</p>
          <select v-model="valorSelect" class="bg-gray-200 rounded-md p-1 text-sm w-1/2 mt-1 border border-gray-300 focus:outline-none focus:border-blue-500">
            <option disabled value="">Selecione</option>
            <option v-for="opcao in opcoes" :value="opcao.valor">{{ opcao.titulo }}</option>
          </select>
      
        <button @click="pesquisar" class="bg-blue-600 rounded-md text-white text-xs p-2 w-1/3 mt-5 hover:bg-blue-400">Calcular</button>
        <p v-if="resultado" class="text-red-500 mt-5 text-center text-sm">Você precisa fazer <strong>{{ resultado }}g</strong> para {{ resultadoDias }} dias.</p>
      </div>
    </div>
</template>