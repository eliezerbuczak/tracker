<template>
    <div class="box">
      <div class="columns">
        <div class="column is-8" role="form">
          <input type="text" class="input" v-model="descricao">
        </div>
        <div class="column">
          <TemporizadoR @aoTemporizadorFinalizado="finalizarTarefa"/>
        </div>
      </div>
    </div>
</template>

<script lang="ts">
import {defineComponent} from "vue";
import TemporizadoR from "@/components/TemporizadoR.vue";
export default defineComponent({
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'FormulariO',
  components: {TemporizadoR},
  emits:['aoSalvarTarefa'],
  data (){
    return{
      descricao : ''
    }
  },
  methods:{
    finalizarTarefa(tempoDecorrido : number ): void{
      this.$emit('aoSalvarTarefa', {
        duracaoEmSegundos: tempoDecorrido,
        descricao:this.descricao
      })
      this.descricao = ''
    }
  }
})
</script>
<style>

</style>