
<template>
    <div class="box formulario">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulario para de uma task">
                <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?" v-model="descricao" />
            </div>

            <div class="column">
               <MyTemporizador @aoTemporizadorFinalizado="finalizarTarefa"/>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from "@vue/runtime-core";
import MyTemporizador from "./MyTemporizador.vue";


export default defineComponent({
    name: "MyFormulario",
    emits:  ['aoSalvarTarefa'],
    components: { MyTemporizador },

    data() {
        return { 
            descricao: ''
        }
    },

    methods:{ 
        
        finalizarTarefa(tempoDecorrido:number) :void {

        this.$emit('aoSalvarTarefa', {
            
            duracaoEmSegundos: tempoDecorrido,
            descricao: this.descricao
        })
        this.descricao = ''

        }
    }
});
</script>

<style>

.formulario{
    color: var(--texto-primario);
    background-color: var(--bg-primario);
}
</style>