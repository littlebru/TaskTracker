<template>
  <main class="columns is-gapless is-multiline">

    <div class="column is-one-quarter">
      <BarraLateral />
    </div>

    <div class="column is-three-quarter">
      <Formulario @aoSalvarTarefa="salvarTarefa"/>

      <div class="lista">
        <Tarefa v-for="(tarefa, index) in ListaDeTarefas" :key="index" :tarefa="tarefa"/>
      </div>

    </div>
  </main>  
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue'
import Formulario from './components/Formulario.vue'
import Tarefa from './components/Tarefa.vue'
import ITarefa from './Interfaces/ITarefa'

export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    Formulario,
    Tarefa
  },
  data() {
    return {
      ListaDeTarefas: [] as ITarefa[]
    }
  },
  methods: {
    salvarTarefa (tarefa: ITarefa){
      this.ListaDeTarefas.push(tarefa)
    }
  }
});
</script>

<style>
  # Formatação da lista de tarefas
  .lista{
    padding: 1.25rem;
  }

</style>
