<template>
    <div class="box formulario">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
                <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?" v-model="descricao">
            </div>
            <div class="column">
                <temporizador @temporizadorFinalizado="finalizarTarefa" />
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import temporizador from '../components/temporizador.vue'

export default defineComponent({
    name: 'formulario',
    components: { temporizador },
    emits: ['salvarTarefa'],
    data() {
        return {
            descricao: ''
        }
    },
    methods: {
        finalizarTarefa(tempoDecorrido: number): void {
            this.$emit('salvarTarefa', {
                duracaoSegundos: tempoDecorrido,
                descricao: this.descricao
            })
            this.descricao = ''
        }
    }
})
</script>

<style>
.formulario {
    color: var(--texto-primario);
    background-color: var(--bg-primario);
}
</style>