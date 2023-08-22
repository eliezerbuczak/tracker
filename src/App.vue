<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <BarraLateral />
    </div>
    <div class="column is-three-quarter">
      <Formulario @aoSalvarTarefa="salvarTarefa"/>
      <div class="lista">
        <TarefA v-for="(tarefa,index) in tarefas" :key="index" :tarefa="tarefa"/>
        <BoX v-if="listEstaVazia">
          Você não está muito produtivo hoje :(
        </BoX>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from "@/components/BarraLateral.vue";
import Formulario from "@/components/FormulariO.vue";
import TarefA from "@/components/TarefA.vue";
import ITarefa from "@/interfaces/ITarefa";
import BoX from "@/components/BoX.vue";

export default defineComponent({
  name: 'App',
  data(){
    return {
      tarefas: [] as ITarefa[]
    }
  },
  computed:{
    listEstaVazia():boolean{
      return this.tarefas.length === 0
    }
  },
  methods:{
    salvarTarefa(tarefa : ITarefa){
      this.tarefas.push(tarefa)
    }
  },
  components: {BoX, TarefA, Formulario, BarraLateral}
});
</script>

<style>
.lista{
  padding: 1.25rem;
}
</style>
