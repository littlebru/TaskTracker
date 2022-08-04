<template>
    <div class="box has-text-weight-bold">
    <!-- A tag slot coloca o conteudo de algum componente que importe o Box, para dentro da tag do componente Box-->
        <slot/>
    </div>
</template>

<script lang="ts">
    import{ defineComponent} from 'vue'

/* eslint-disable */
    export default defineComponent({
        name: 'Box'
    });
</script>


<!--Escopado significa que ele só vai ser aplicado neste componente especifico ou para os filhos dele-->
<style scoped>
    .box{
        background: #FFBD59;
    }
</style>