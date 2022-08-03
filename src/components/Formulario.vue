<template>
    <div class="box">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulario para criacao de tarefas">

                <input 
                type="text" 
                class="input" 
                placeholder="Qual tarefa voce deseja iniciar?"
                v-model="descricao"/>

            </div>
            <Temporizador @aoTemporizadorFinalizado="finalizarTarefa"/>
        </div>
    </div>
</template>


<script lang="ts">

    import{ defineComponent} from 'vue'
    import Temporizador from './Temporizador.vue'

/* eslint-disable */
    export default defineComponent({
        name: 'Formulario',
        emits:[
            'aoSalvarTarefa'
        ],
        components:{
            Temporizador
        },
        data () {
            return {
                descricao: ''
            }
        },
        methods: {
            // registro da tarefa descrita
            finalizarTarefa (tempoDecorridoFormatado: number) : void {
                this.$emit('aoSalvarTarefa', {
                    duracaoEmSegundos: tempoDecorridoFormatado,
                    descricao: this.descricao
                })
                // Limpar o campo de descricao da tarefa
                this.descricao = ''
            }
        }
    });
</script>