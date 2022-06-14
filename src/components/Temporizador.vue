<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
        <!-- Cronometro -->
        <Cronometro :tempoEmSegundos="tempoEmSegundos" />

        <!-- Botão play -->
        <Botao @clicado="iniciarContagem" :desabilitado="cronometroRodando" :icone="'fa-solid fa-play play'" :texto="'Play'"/>

        <!-- Botão stop -->
        <Botao @clicado="finalizarContagem" :desabilitado="!cronometroRodando" icone="fas fa-stop stop" texto="Stop"/>
    </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Cronometro from './Cronometro.vue';
import Botao from './Botao.vue'

export default defineComponent({
    name: "TemporizadorFormulario",
    emits: ['aoTemporizadorFinalizado'],
    methods: {
        iniciarContagem(): void {
            console.log("Iniciando");
            
            this.cronometroRodando = true;
            this.idCoronemtro = setInterval(() => {
                this.tempoEmSegundos += 1;
            }, 1000);
        },
        finalizarContagem(): void {
            console.log("Finalizando");
            clearInterval(this.idCoronemtro);
            this.cronometroRodando = false;
            this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos);
            this.tempoEmSegundos = 0;
        }
    },
    data() {
        return {
            tempoEmSegundos: 0,
            idCoronemtro: 0,
            cronometroRodando: false
        }
    },
    components: {
        Cronometro,
        Botao
    }
})
</script>