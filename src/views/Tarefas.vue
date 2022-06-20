<template>
    <Formulario @aoSalvarTarefa="salvarTarefa"/>
    <div class="lista">
        <Box v-if="isEmpty">Nenhuma Tarefa Adicionada</Box>
        <Tarefa @aoExcluirTarefa="excluirTarefa" v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
    </div> 
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import ITarefa from '../interfaces/ITarefas';
import Formulario from '../components/Formulario.vue';
import Tarefa from '../components/Tarefa.vue';
import Box from '../components/Box.vue';

export default defineComponent({
  name: 'App',
  components: {
    Formulario,
    Tarefa,
    Box
  },
  data(){
    return{
      tarefas: [] as ITarefa[]
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
    }
  }
});
</script>

<style>
.lista{
  padding: 1.25rem;
}
</style>
