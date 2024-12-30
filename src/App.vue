<script setup>
import { ref, computed, watch, onMounted } from 'vue';

const nome = ref('')
const lista_tarefas = ref([])

const conteudo_input = ref('')
const adicionarTarefa = () => {
  if (conteudo_input.value.trim() === '') return
  lista_tarefas.value.push({
    id: Date.now(),
    conteudo: conteudo_input.value,
    created_at: Date.now()
  })
  conteudo_input.value = ''
}
const lista_tarefas_asc = computed(() => lista_tarefas.value.sort((a, b) => {
  return b.created_at - a.created_at
})) // Ordena a lista de tarefas em ordem de criação (ascendente)

watch(nome, (newval) => {localStorage.setItem('nome', newval)})
onMounted(() => {nome.value = localStorage.getItem('nome') || ''})
</script>

<template>

  <main class="app">
    <section class="saudacao">
      <h2 class="titulo">
        Seja bem vindo, <input type="text" placeholder="Digite seu nome" v-model="nome" />
      </h2>
    </section>
  </main>

  <section class="criar-tarefa">
    <h3>Criar tarefa</h3>
    <form @sumbimt.prevent="adicionarTarefa" class="action">
      <h4>Conteúdo</h4>
      <input
        type="text"
        placeholder="por exemplo: Comprar pão"
        v-model="conteudo_input"
      />
    </form>

  </section>

</template>

<style scoped></style>
