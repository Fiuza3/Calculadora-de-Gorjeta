<template>
  <v-container class="mt-10" max-width="500px">
    <v-card-title class="text-h5">Calculadora de Gorjeta</v-card-title>
    <v-card class="pa-5" elevation="6">
      <v-text-field
        v-model="valorConta"
        label="Valor da Conta (R$)"
        type="number"
        outlined
        class="mb-4"
      />
      <v-text-field
        v-model="porcentagemGorjeta"
        label="Porcentagem da Gorjeta (%)"
        type="number"
        outlined
        class="mb-4"
      />
      <v-text-field
        v-model="quantidadePessoas"
        label="Número de Pessoas"
        type="number"
        outlined
        class="mb-4"
      />

      <v-divider class="my-4" />

      <div>Valor da Gorjeta: R$ {{ valorGorjeta }}</div>
      <div>Total com Gorjeta: R$ {{ totalComGorjeta }}</div>
      <div>Valor por Pessoa: R$ {{ valorPorPessoa }}</div>
    </v-card>
  </v-container>
</template>

<script setup>
// Importa o que precisamos do Vue
import { ref, computed } from 'vue'

// Aqui criamos as variáveis que guardam o que o usuário digita
const valorConta = ref(0)
const porcentagemGorjeta = ref(10)
const quantidadePessoas = ref(1)

// Aqui a gente calcula quanto vai ser a gorjeta
const valorGorjeta = computed(() => {
  return ((valorConta.value * porcentagemGorjeta.value) / 100).toFixed(2)
})

// Aqui soma o valor da conta com a gorjeta
const totalComGorjeta = computed(() => {
  return (parseFloat(valorConta.value) + parseFloat(valorGorjeta.value)).toFixed(2)
})

// Aqui divide o total entre o número de pessoas
const valorPorPessoa = computed(() => {
  return (totalComGorjeta.value / quantidadePessoas.value).toFixed(2)
})
</script>
