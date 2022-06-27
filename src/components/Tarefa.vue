<template>
    <Box>
        <div class="columns">
            <div class="column is-6">
                {{ tarefa.descricao || "Tarefa sem descrição" }}
            </div>
            <div class="column is-4">
                <Cronometro :tempoEmSegundos="tarefa.duracaoEmSegundos"/>
            </div>
            <div class="column is-2">
                <Botao @clicado="excluirTarefa" :desabilitado="false" :icone="'fa-solid fa-xmark close'" :texto="'Excluir'"/>
            </div>
        </div>    
    </Box>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';
import ITarefa from '../interfaces/ITarefa'
import Cronometro from './Cronometro.vue';
import Box from './Box.vue';
import Botao from './Botao.vue';

export default defineComponent({
    name: 'TarefasFormulario',
    emits: ['aoExcluirTarefa'],
    props: {
        tarefa:{
            type: Object as PropType<ITarefa>,
            required: true
        }
    },
    components:{
        Cronometro,
        Box,
        Botao
    },
    methods: {
        excluirTarefa(): void{
            this.$emit('aoExcluirTarefa', this.tarefa);
        }
    }
});
</script>
