<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <CronometrO :tempoEmSegundosCronometro="tempoEmSegundos" />
    <ButtoN @clicado="iniciar" icone="fas fa-stop" texto="Start" :desabilitado="cronometroRodando" />
    <ButtoN @clicado="finalizar" icone="fas fa-stop" texto="Stop" :desabilitado="!cronometroRodando" />

  </div>
</template>

<script lang="ts">
import {defineComponent} from "vue";
import CronometrO from "@/components/CronometrO.vue";
import ButtoN from "@/components/ButtoN.vue";
export default defineComponent({
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'TemporizadoR',
  emits:['aoTemporizadorFinalizado'],
  components: {ButtoN, CronometrO},
  data(){
    return {
      cronometro: 0,
      tempoEmSegundos: 0,
      cronometroRodando: false
    }
  },
  methods:{
    iniciar(){
      this.cronometroRodando = true
      this.cronometro = setInterval(()=>{
        this.tempoEmSegundos++
      },1000)
    },
    finalizar(){
      this.cronometroRodando = false
      clearInterval(this.cronometro)
      this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos)
      this.tempoEmSegundos = 0
    }
  }

})
</script>