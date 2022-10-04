<template>
    <header>
        <div class="logo" style="display:flex;justify-content:center">
            <img src="../assets/logo.png" alt=""/>
        </div >
        <div style="display:flex;justify-content:center">
            <button class="button" @click="alterarTema">
                {{textoBotao}}
            </button>

        </div>
    </header>

</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name:'BarraLateral',
    emits:[
        'aoTemaAlterado'
    ],
    data(){
       return {    
        modoEscuroAtivo: false
    };
    },
    methods:{
        alterarTema(){
            this.modoEscuroAtivo = !this.modoEscuroAtivo
            this.$emit('aoTemaAlterado',this.modoEscuroAtivo);
        }
    },
    computed:{
        textoBotao(){
            if(this.modoEscuroAtivo){
                return 'Ativar modo claro'
            }
            else{
                return 'Ativar modo escuro'
            }
        }
    }
});
</script>


<style scoped>
    header{
        background: #0d3b66;
        width: 100%;
        height: 100vh;
    }
    @media only screen and (max-width:768px){

        header{
            padding: 2.5rem;
            height: auto;
        }
        .logo{
            display: flex !important;
            justify-content: center !important;
            align-items: center !important;
        }

    }
</style>