<template>
  <BoX>
    <div class="columns">
      <div class="column is-7">
        {{ tarefa.descricao }}
      </div>
      <div class="column">
        <CronometrO :tempoEmSegundosCronometro="tarefa.duracaoEmSegundos"/>
      </div>
    </div>
  </BoX>
</template>
<script lang="ts">
import {defineComponent, PropType} from "vue";
import CronometrO from "@/components/CronometrO.vue";
import ITarefa from "@/interfaces/ITarefa";
import BoX from "@/components/BoX.vue";

export default defineComponent({
  name: 'TarefA',
  props:{
    tarefa:{
      type: Object as PropType<ITarefa>,
      required: true
    }
  },
  components: {BoX, CronometrO}
})
</script>

<style scoped>
</style>