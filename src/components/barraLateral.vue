<template>
  <header>
    <h1>
      <img src="../assets/logo.png">
    </h1>
    <button class="button" @click="alterarTema">
      {{ textoBotao }}
    </button>
  </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'barraLateral',
  emits: ['temaAlterado'],
  data() {
    return {
      modoEscuro: false
    }
  },
  computed: {
    textoBotao(): string {
      return this.modoEscuro ? 'Ativar modo claro ' : 'Ativar modo escuro'
    }
  },
  methods: {
    alterarTema() {
      this.modoEscuro = !this.modoEscuro
      this.$emit('temaAlterado', this.modoEscuro)
    }
  }
})
</script>

<style scoped>
header {
  padding: 1rem;
  background: #0d3b66;
  width: 100%;
  height: 100vh;
  text-align: center;
}

@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
</style>./barraLateral.vue