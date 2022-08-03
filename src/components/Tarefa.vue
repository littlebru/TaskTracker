<template>
    <div class="box has-text-weight-bold">
        <div class="columns">
            <div class="column is-7">
                {{tarefa.descricao}}
            </div>
            <div class="column">
                <Cronometro :tempo="tarefa.duracaoEmSegundos"/>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
    import{ defineComponent, PropType} from 'vue'
    import Cronometro from './Cronometro.vue'
    import ITarefa from '../Interfaces/ITarefa'

    /* eslint-disable */
    export default defineComponent({
        name: 'Tarefa',
        components:{
            Cronometro
        },
        props:{
            tarefa: {
                type: Object as PropType<ITarefa>,
                required: true
            }
        }
    });
</script>

<!--Escopado significa que ele só vai ser aplicado neste componente especifico ou para os filhos dele-->
<style scoped>
    .box{
        background: #FFBD59;
    }
</style>