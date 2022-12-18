<template>
    <div class="box formulario">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
                <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?" v-model="descricao" />
            </div>
            <div class="column">
                <Temporizador @finalizar="finalizarTarefa" />
            </div>
        </div>
    </div>
</template>
  
<script lang="ts">
import { defineComponent } from "vue";
import Temporizador from "./Temporizador.vue";
export default defineComponent({
    name: "Formulário",
    emits: ['adicionarTarefa'],
    components: {
        Temporizador
    },
    data() {
        return {
            descricao: ''
        }
    },
    methods: {
        finalizarTarefa(tempoEmSegundos: number): void {
            this.$emit('adicionarTarefa', {
                descricao: this.descricao,
                duracaoEmSegundos: tempoEmSegundos
            })
            this.descricao = ''
        }
    }
});
</script>

<style>
.formulario {
    color: var(--texto-primario);
    background: var(--bg-primario);
}
</style>