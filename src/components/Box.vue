<template>
    <div class="box has-text-weight-bold" :style="estilos">
    <!-- A tag slot coloca o conteudo de algum componente que importe o Box, para dentro da tag do componente Box-->
        <slot/>
    </div>
</template>

<script lang="ts">
    import{ defineComponent} from 'vue'

/* eslint-disable */
    export default defineComponent({
        name: 'Box',
        data () {
            return {
                estilos: {
                    backgroundColor: '#FFBD59'
                }
            }
        }
    });
</script>