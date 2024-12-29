<script setup>
import { ref, computed } from 'vue';

const nome = ref('')
const lista_tarefas = ref([])

const conteudo_input = ref('')
const lista_tarefas_asc = computed(() => lista_tarefas.value.sort((a, b) => {
  return b.created_at - a.created_at
})) // Ordena a lista de tarefas em ordem de criação (ascendente)
</script>

<template>

  <main class="app">
    <section class="saudacao">
      <h2 class="titulo">
        Seja bem vindo, <input type="text" placeholder="Digite seu nome" v-model="nome" />
      </h2>
    </section>
  </main>

</template>

<style scoped></style>
