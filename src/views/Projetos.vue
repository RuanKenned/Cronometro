<template>
    <section class="projetos">
        <h1 class="title">Projetos</h1>
        <form @submit.prevent="salvar">
            <div class="field">
                <label for="nomeProjeto" class="label">Nome do Projeto</label>
                <input type="text" class="input" v-model="nomeProjeto" id="nomeProjeto"/>
            </div>
            <div class="field">
                <button class="button" type="submit">
                    Salvar
                </button>
            </div>
        </form>
        <table class="table is-fullwidth">
            <thead>
                <th>ID</th>
                <th>Nome</th>
            </thead>
            <tbody>
                <tr v-for="projeto in projetos" :key="projeto.id">
                    <td>{{ projeto.id }}</td>
                    <td>{{ projeto.nome }}</td>
                </tr>
            </tbody>
        </table>
    </section>
</template>

<script lang="ts">
import { meuUseStore } from "@/store";
import { computed, defineComponent } from "vue";

export default defineComponent({
    name: 'ProjetosView',
    data(){
        return{
            nomeProjeto: ''
        }
    },
    methods: {
        salvar(){
            this.store.commit('ADICIONA_PROJETO', this.nomeProjeto);
            this.nomeProjeto = '';
        }
    },
    setup(){
        const store = meuUseStore();
        return {
            store,
            projetos: computed(() => store.state.projetos)
        }
    }
});
</script>

<style scoped>
.projetos{
    padding: 1.25rem
}
</style>