<template>
    <BoxCurso class="grid box-tarefa">
        <div class=""> {{tarefa.descricao||'Tarefa sem descrição'}}</div>
        <div class="">
            <CronometroCurso :tempoEmSegundos="tarefa.duracaoEmSegundos" />
        </div>
    </BoxCurso>


</template>

<script lang="ts">
import ITarefa from '@/interfaces/ITarefa';
import { defineComponent, PropType } from 'vue';
import CronometroCurso from './CronometroCurso.vue'
import BoxCurso from './BoxCurso.vue'
export default defineComponent({
    name: 'TarefaCurso',
    components: {
        CronometroCurso,
        BoxCurso
    },
    props: {
        tarefa: {
            type: Object as PropType<ITarefa>
            , required: true
        }
    }

})
</script>


<style>
.grid {
    display: grid;
    grid-template-columns: 90% 10%;
}

.box-tarefa {
    margin: 10px;
    background-color: #FAF0CA;
}
</style>