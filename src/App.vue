<template>
  <main class="columns is-gapless is-multiline " :class="{'modo-escuro':modoEscuroAtivo}">
    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema"/>
    </div>
    <div class="column is-three-quarter conteudo">
      <FormularioBarra @aoSalvarTarefa="salvarTarefa" />
      <div class="lista">
        <TarefaCurso v-for="(tarefa,index) in tarefas" :key="index" :tarefa="tarefa" />
        <BoxCurso v-if="tarefas.length==0">
          Você não está muito produtivo hoje

        </BoxCurso>
      </div>
    </div>

  </main>

</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue'
import FormularioBarra from './components/FormularioBarra.vue'
import TarefaCurso from './components/TarefaCurso.vue'
import ITarefa from './interfaces/ITarefa';
import BoxCurso from './components/BoxCurso.vue';
export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    FormularioBarra,
    TarefaCurso,
    BoxCurso
},
  data() {
    return {
      tarefas: [] as ITarefa[],
      modoEscuroAtivo:false

    }

  }
  ,
  methods: {
    salvarTarefa(tarefa: ITarefa) {
      this.tarefas.push(tarefa)
      console.log(this.tarefas)

    },
    trocarTema(modoEscuroAtivo:boolean){
      console.log(modoEscuroAtivo)
      this.modoEscuroAtivo=!this.modoEscuroAtivo
    }
  }
});
</script>

<style>
  main{
    --bg-primario:#fff;
    --texto-primario:#000;
  }
  main.modo-escuro{
    --bg-primario:#2b2d42;
    --texto-primario:#ddd;
  }
  .conteudo{
    background-color: var(--bg-primario);
  }

</style>
