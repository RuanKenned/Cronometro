<template>
    <section>
        <strong>
            {{ tempoDecorrido }}
        </strong>
    </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: "CronometroFormulario",
    props: {
        tempoEmSegundos: {
            type: Number,
            dafault: 0
        }
    },
    computed: {
        tempoDecorrido(): string {
            return new Date(Number(this.tempoEmSegundos) * 1000).toISOString().substring(11, 19);
        }
    }
})
</script>

<style>
</style>