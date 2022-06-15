<template>
  <main class="columns is-gapless is-multiline" :class="{'modo-escuro':modoEscuroAtivo}">

    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="alterarTema"/>
    </div>

    <div class="column is-three-quarter conteudo">
      <Formulario @aoSalvarTarefa="salvarTarefa"/>
      <div class="lista">
        <Box v-if="isEmpty">Nenhuma Tarefa Adicionada</Box>
        <Tarefa @aoExcluirTarefa="excluirTarefa" v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
      </div>
    </div>

  </main>  
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import ITarefa from './interfaces/ITarefas';
import BarraLateral from './components/BarraLateral.vue';
import Formulario from './components/Formulario.vue';
import Tarefa from './components/Tarefa.vue';
import Box from './components/Box.vue';

export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    Formulario,
    Tarefa,
    Box
  },
  data(){
    return{
      tarefas: [] as ITarefa[],
      modoEscuroAtivo: false
    }    
  },
  computed:{
    isEmpty(): boolean{
      return this.tarefas.length === 0
    }
  },
  methods: {
    salvarTarefa(tarefa: ITarefa){
      this.tarefas.push(tarefa);
    },
    excluirTarefa(tarefa: ITarefa): void{
      var index = this.tarefas.indexOf(tarefa);
      this.tarefas.splice(index, 1);
    },
    alterarTema(isModoEscuro: boolean): void{
      this.modoEscuroAtivo = isModoEscuro;
    }
  }
});
</script>

<style>
.lista{
  padding: 1.25rem;
}

main{
  --bg-primario: #FFF;
  --texto-primario: #000;
}

main.modo-escuro{
  --bg-primario: #2b2d42;
  --texto-primario: #ddd;
}

.conteudo{
  background-color: var(--bg-primario);
}
</style>
