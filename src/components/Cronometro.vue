<template>
     <section class="cronometro">
        <strong>
        {{ tempoDecorridoFormatado }}
        </strong>
    </section>
</template>

<script lang= "ts">
     import{ defineComponent} from 'vue'
/* eslint-disable */
    export default defineComponent({
        name: 'Cronometro',
        props: {
            tempo: {
                type: Number,
                default: 0
            }
        } ,
        computed: {
            tempoDecorridoFormatado () : string  {
                // Mais sobre a biblioteca de Data (https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Date)
                // new Date().toLocaleTimeString() - retorna o horario localizado de acordo com o idioma do navegador
                // new Date().toISOString() - retorna uma string respeitando a ISO (https://en.wikipedia.org/wiki/ISO_8601)
                return new Date(this.tempo * 1000).toISOString().substring(19, 11);
            }
        },
    })
</script>

<!--Escopado significa que ele só vai ser aplicado neste componente especifico ou para os filhos dele-->
<style scope>
 .cronometro strong{
     color: var(--texto-primario);
 }
</style>