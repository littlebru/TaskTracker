<template>
    <Box>
        <div class="columns tarefa">
            <div class="column is-7 descricao">
                {{tarefa.descricao || 'Tarefa sem descrição'}}
            </div>
            <div class="column tarefa">
                <Cronometro :tempo="tarefa.duracaoEmSegundos" class="tarefa"/>
            </div>
        </div>
    </Box>
</template>

<script lang="ts">
    import{ defineComponent, PropType} from 'vue'
    import Cronometro from './Cronometro.vue'
    import ITarefa from '../Interfaces/ITarefa'
    import Box from './Box.vue'

    /* eslint-disable */
    export default defineComponent({
        name: 'Tarefa',
        components:{
            Cronometro,
            Box
        },
        props:{
            tarefa: {
                type: Object as PropType<ITarefa>,
                required: true
            }
        }
    });
</script>

<style scope>
 .tarefa{
     color: var(--texto-primario);
     font-weight: normal;
 }
 .descricao {
     padding-left: 0.5rem;
     text-transform: capitalize;
 } 
</style>