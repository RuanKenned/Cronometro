<template>
    <div class="box">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
                <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?" v-model="descricao">
            </div>
            <div class="column is-4">
                <!-- Temporizador -->
                <TemporizadorFormulario @aoTemporizadorFinalizado="finalizarTarefa"/>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import TemporizadorFormulario from './Temporizador.vue'

export default defineComponent({
    name: 'FormularioBasico',
    data(){
        return {
            descricao: ''
        }
    },
    components: {
        TemporizadorFormulario
    },
    methods:{
        finalizarTarefa(tempoDecorrido: number):void{
            console.log(this.descricao, " - ", tempoDecorrido);
            this.descricao = "";
        }
    }
})
</script>

<style>
</style>