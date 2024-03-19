<template>
  <main class="columns is-gapless is-multiline" :class="{'modo-escuro': modoEscuro}">
    <div class="column is-one-quarter">
      <barra-lateral @temaAlterado="alterarTema" />
    </div>
    <div class="column is-three-quarter conteudo">
      <formluario @salvarTarefa="salvarTarefa" />
      <div class="lista">
        <tarefa v-for="(tarefa, i) in tarefas" :key="i" :tarefa="tarefa" />
        <box v-if="listaVazia">
          Você não está muito produtivo hoje :(
        </box>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import barraLateral from './components/barraLateral.vue'
import formluario from './components/formulario.vue'
import tarefa from './components/tarefa.vue'
import ITarefa from './interfaces/ITarefa'
import box from './components/box.vue'

export default defineComponent({
  name: 'App',
  components: {
    barraLateral,
    formluario,
    tarefa,
    box
  },
  data() {
    return {
      tarefas: [] as ITarefa[],
      modoEscuro: false
    }
  },
  computed: {
    listaVazia(): boolean {
      return this.tarefas.length === 0
    }
  },
  methods: {
    salvarTarefa(tarefa: ITarefa) {
      this.tarefas.push(tarefa)
    },
    alterarTema(modoEscuro: boolean){
      this.modoEscuro = modoEscuro
    }
  }
});
</script>

<style>
.lista {
  padding: 1.25rem;
}

main {
  --bg-primario: #fff;
  --texto-primario: #000;
}

main.modo-escuro {
  --bg-primario: #2b2d42;
  --texto-primario: #ddd;
}

.conteudo {
  background-color: var(--bg-primario);
}
</style>
