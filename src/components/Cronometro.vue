<template>
     <section>
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
                return new Date(this.tempo * 1000).toISOString().substring(19, 11);
            }
        },
    })
</script>
