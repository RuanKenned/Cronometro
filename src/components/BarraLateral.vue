<template>
  <header>
    <h1>
      <img src="../assets/logo.png" alt="">
    </h1>
    <button class="button" @click="alterarTema">
      {{ textoBotaoTema }}
    </button>
  </header>
</template>

<script lang="ts">
import {defineComponent} from 'vue';
  
export default defineComponent ({
  name: 'BarraLateral',
  emits: ['aoTemaAlterado'],
  data(){
    return {
      isModoEscuro: false
    }
  },
  methods: {
    alterarTema(){
      this.isModoEscuro = !this.isModoEscuro;
      this.$emit('aoTemaAlterado', this.isModoEscuro);
    }
  },
  computed: {
    textoBotaoTema(){
      if(this.isModoEscuro){
        return 'Desativar Modo Escuro';
      }else{
        return 'Ativar Modo Escuro';
      }
    }
  }
})
</script>

<style>
header {
  padding: 1rem;
  background: #0d3b66;
  width: 100%;
  height: 100vh;
  text-align: center;
}

@media only screen and (max-width: 768px) {
  header{
    padding: 2.5rem;
    height: auto;
  }
}
</style>