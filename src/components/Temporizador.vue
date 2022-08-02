<template>      
    <div class="column">
        <div class="is-flex is-align-items-center is-justify-content-space-between">

            <Cronometro :tempo = "tempo"/>

            <button class="button" @click="iniciar" :disabled="cronometroRodando">
                <span class="icon">
                    <i class="fas fa-play"></i>
                </span>
                <span>play</span>
            </button>
            <button class="button" @click="finalizar" :disabled="!cronometroRodando">
                <span class="icon">
                    <i class="fas fa-stop"></i>
                </span>
                <span>stop</span>
            </button>
        </div>
    </div>
</template>



<script lang="ts">

    import{ defineComponent} from 'vue'
    import Cronometro from './Cronometro.vue'
/* eslint-disable */
    export default defineComponent({
        name: 'Temporizador',
        components:{
            Cronometro
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
            }
        }
    });
</script>