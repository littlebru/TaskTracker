<template>
  <main class="columns is-gapless is-multiline" :class="{ 'modo-escuro': modoEscuroAtivo }">

    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema" />
    </div>

    <div class="column is-three-quarter conteudo">
      <Formulario @aoSalvarTarefa="salvarTarefa"/>
      
      <div class="lista">
        <Tarefa v-for="(tarefa, index) in ListaDeTarefas" :key="index" :tarefa="tarefa"/>

        <Box v-if="listaEstaVazia">
          <h3 align="center">Você não possui tarefas registradas :(</h3>
        </Box>

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
import Box from './components/Box.vue'

export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    Formulario,
    Tarefa,
    Box
  },
  data() {
    return {
      ListaDeTarefas: [] as ITarefa[],
      modoEscuroAtivo: false
    }
  },
  computed:{
    listaEstaVazia () : boolean {
      return this.ListaDeTarefas.length === 0
    }
  },
  methods: {
    salvarTarefa (tarefa: ITarefa){
      this.ListaDeTarefas.push(tarefa)
    },
    trocarTema(modoEscuroAtivo: boolean){
        this.modoEscuroAtivo = modoEscuroAtivo
    }
  }
});
</script>

<style>
  # Formatação da lista de tarefas
  .lista{
    padding: 1.25rem;
  }

  main {
    --bg-primario: #fff;
    --texto-primario: #333;
  }

  main.modo-escuro{
    --bg-primario: #333;
    --texto-primario: #fff;
    --bg-primario-form: #222;
  }

  .conteudo{
    background-color: var(--bg-primario);
  }

</style>
