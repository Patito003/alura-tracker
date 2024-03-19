<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <cronometro :tempoSegundos="tempoSegundos" />
    <button class="button" @click="iniciar" :disabled="cronometroRunning">
      <span class="icon">
        <i class="fas fa-play"></i>
      </span>
      <span>play</span>
    </button>
    <button class="button" @click="finalizar" :disabled="!cronometroRunning">
      <span class="icon">
        <i class="fas fa-stop"></i>
      </span>
      <span>stop</span>
    </button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import cronometro from '../components/cronometro.vue'

export default defineComponent({
  name: 'temporizador',
  components: { cronometro },
  emits: ['temporizadorFinalizado'],
  data() {
    return {
      tempoSegundos: 0,
      cronometro: 0,
      cronometroRunning: false
    }
  },
  methods: {
    iniciar() {
      this.cronometroRunning = true
      this.cronometro = setInterval(() => {
        this.tempoSegundos++
      }, 1000)

    },
    finalizar() {
      this.cronometroRunning = false
      clearInterval(this.cronometro)
      this.$emit('temporizadorFinalizado', this.tempoSegundos)
      this.tempoSegundos = 0
    }
  }
})
</script>

<style scoped></style>