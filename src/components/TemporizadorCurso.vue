<template>

<div class="is-flex is-align-items-center is-justify-content-space-between">
                    <CronometroCurso :tempoEmSegundos="tempoEmSegundos"></CronometroCurso>
 
                    <button class="button" @click="iniciar()" :disabled="running">
                        <span class="icon">
                            <i class="fas fa-play"></i>
                        </span>
                        <span>play</span>
                    </button>
                    <button class="button" @click="finalizar()" :disabled="!running">
                        <span class="icon">
                            <i class="fas fa-stop"></i>
                        </span>
                        <span>stop</span>
                    </button>
                </div>


</template>

<script lang="ts">
import { defineComponent } from 'vue';
import CronometroCurso from './CronometroCurso.vue'

export default defineComponent({
    name:'TemporizadorCurso',
    emits:[
        'aoTemporizadorFinalizado'
    ],
    data(){
        return {
            tempoEmSegundos:0,
            cronometro:0,
            canRun:true,
            running:false
        } 
    },
    components:{
        CronometroCurso
    },
    computed:{

    },
    methods:{
        iniciar(){
            if(this.canRun){
                this.running = true
                this.cronometro =  setInterval(()=>{
                    this.tempoEmSegundos++
                },1000)
                
                this.canRun = false
            }

        },
        finalizar(){
            if(this.running){
                this.canRun = true
                clearInterval(this.cronometro)
                this.running = false;
                this.$emit('aoTemporizadorFinalizado',this.tempoEmSegundos)
                this.tempoEmSegundos = 0;
            }
        }
    }
});

</script>