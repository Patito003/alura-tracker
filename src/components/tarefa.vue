<template>
  <box>
    <div class="columns">
      <div class="column is-7">
        {{ tarefa.descricao || 'Tarefa sem descrição' }}
      </div>
      <div class="column">
        <cronometro :tempoSegundos="tarefa.duracaoSegundos" />
      </div>
    </div>
  </box>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue'
import cronometro from './cronometro.vue'
import ITarefa from '../interfaces/ITarefa'
import box from './box.vue'

export default defineComponent({
  name: 'tarefa',
  components: { cronometro, box },
  props: {
    tarefa: {
      type: Object as PropType<ITarefa>,
      required: true
    }
  }

})
</script>
