<template>
  <section class="is-flex is-align-items-center is-justify-content-space-between">
    <Cronometro :tempo="tempo"/>
    <Botao @clicado="iniciar" icone="fas fa-play" texto="play" :desabilitado="cronometroRodando" />
    <Botao @clicado="finalizar" icone="fas fa-stop" texto="stop" :desabilitado="!cronometroRodando" />
  </section>
</template>



<script lang="ts">

    import{ defineComponent} from 'vue'
    import Cronometro from './Cronometro.vue'
    import Botao from './Botao.vue'

/* eslint-disable */
    export default defineComponent({
        name: 'Temporizador',
        emits:['aoTemporizadorFinalizado'],
        components:{
            Cronometro,
            Botao
        },
        data () {
            return {
                tempo: 0,
                cronometro: 0,
                cronometroRodando: false
            }
        },
        methods: {
            iniciar() {
                console.log('Iniciando');
                // comecar contagem 
                // 1 seg = 1000 ms
                this.cronometro = setInterval(()=> {
                    this.tempo = this.tempo + 1
                }, 1000)
                this.cronometroRodando=true
            },
            finalizar() {
                this.cronometroRodando = false
                // pausar contagem do timer
                clearInterval(this.cronometro)

                // $emit(nome do evento que emite, payload ou carga de dados que vai junto com o evento)
                this.$emit('aoTemporizadorFinalizado', this.tempo)
                
                // resetando o tempo do cronometro
                this.tempo = 0
            }
        }
    });
</script>