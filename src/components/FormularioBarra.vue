<template>
    <div class="box formulario">
        <div class="columns">
            <div class="column is-8" role="form">
                <input type="text" class="input" placeholder="qual tarefa você deseja iniciar?" v-model="descricao" />
            </div>
            <div class="column">
                <TemporizadorCurso @aoTemporizadorFinalizado="finalizarTarefa"></TemporizadorCurso>
            </div>
        </div>
    </div>


</template>

<script lang="ts">
import { defineComponent } from 'vue';
import CronometroCurso from './CronometroCurso.vue'
import TemporizadorCurso from './TemporizadorCurso.vue'
import ITarefa from '@/interfaces/ITarefa';
export default defineComponent({
    name: 'FormularioBarra',
    components: { TemporizadorCurso },
    methods: {
        finalizarTarefa(tempoDecorrido: number) {
            console.log(tempoDecorrido)
            this.$emit('aoSalvarTarefa', { descricao: this.descricao, duracaoEmSegundos: tempoDecorrido })
            this.descricao = ''
        }
    },
    data() {
        return {
            descricao: ''
        }

    },
    emits: ['aoSalvarTarefa'],

})


</script>


<style>
.formulario{
    color:var(--texto-primario);
    background-color: var(--bg-primario );
}
</style>