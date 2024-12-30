<script setup>
import { ref, computed, watch, onMounted } from "vue";

const lista_tarefas = ref([]);
const nome = ref("");
const conteudo_input = ref("");
const adicionar_tarefa = () => {
  if (conteudo_input.value.trim() === "") {
    return;
  } // Não permite adicionar tarefas vazias

  lista_tarefas.value.push({
    conteudo: conteudo_input.value,
    concluido: false, // Inicializa a tarefa como não concluída
    criado_em: Date.now(),
  });
};

const remover_tarefa = (tarefa) => {
  const index = lista_tarefas.value.indexOf(tarefa);
  lista_tarefas.value.splice(index, 1);
};

const lista_tarefas_asc = computed(() =>
  lista_tarefas.value.sort((a, b) => {
    return b.created_at - a.created_at;
  })
); // Ordena a lista de tarefas em ordem de criação (ascendente)

watch(
  lista_tarefas,
  (newval) => {
    localStorage.setItem("lista_tarefas", JSON.stringify(newval));
  },
  { deep: true }
); // Salva a lista de tarefas no localStorage, mesmo que seja inicializada vazia

watch(nome, (newval) => {
  localStorage.setItem("nome", newval);
});
onMounted(() => {
  nome.value = localStorage.getItem("nome") || "";
  lista_tarefas.value = JSON.parse(localStorage.getItem("lista_tarefas")) || [];
}); // Carrega o nome do usuário e a lista de tarefas do localStorage ao iniciar a aplicação
</script>

<template>
  <main class="app">
    <section class="saudacao">
      <h2 class="titulo">
        Seja bem vindo,
        <input type="text" placeholder="Digite seu nome" v-model="nome" />
      </h2>
    </section>
  </main>

  <section class="criar-tarefa">
    <h3>Criar tarefa</h3>

    <form @submit.prevent="adicionar_tarefa">
      <h4>Conteúdo</h4>

      <input type="text" placeholder="Comprar pão" v-model="conteudo_input" />

      <input type="submit" value="Adicionar tarefa" />
    </form>
  </section>

  <section class="lista-tarefas">
    <h3>Lista de tarefas</h3>

    <div class="list">
      <div
        v-for="tarefa in lista_tarefas_asc"
        :class="`item-tarefa ${tarefa.concluido && 'concluido'}`"
      >
        <label>
          <input type="checkbox" v-model="tarefa.concluido" />
          <span class="bubble"></span>
        </label>
        <div class="conteudo-tarefa">
          <input type="text" v-model="tarefa.conteudo" />
        </div>
        <div class="acoes">
          <button class="remover" @click="remover_tarefa(tarefa)">
            Remover
          </button>
        </div>
      </div>

      <div>
        <span
          >Concluídas:
          {{ lista_tarefas_asc.filter((t) => t.concluido).length }}</span
        >
      </div>
      <div>
        <span
          >Pendentes:
          {{ lista_tarefas_asc.filter((t) => !t.concluido).length }}</span
        >
      </div>
    </div>
  </section>
</template>

<style scoped></style>
