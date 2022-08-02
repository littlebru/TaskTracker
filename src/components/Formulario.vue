<template>
    <div class="box">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulario para criacao de tarefas">

                <input 
                type="text" 
                class="input" 
                placeholder="Qual tarefa voce deseja iniciar?"/>

            </div>
            <Temporizador/>
        </div>
    </div>
</template>


<script lang="ts">

    import{ defineComponent} from 'vue'
    import Temporizador from './Temporizador.vue'
/* eslint-disable */
    export default defineComponent({
        name: 'Formulario',
        components:{
            Temporizador
        }
    });
</script>