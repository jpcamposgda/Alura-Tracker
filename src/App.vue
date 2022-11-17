<template>
  <main class="columns is-gapless is-multiline " :class="{'modo-escuro': modoEscuroAtivo}">
    <div class="colum is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema" />
    </div>
    <div class="column is-three-quarter conteudo">
      <MyFormulario @aoSalvarTarefa="salvarTarefa" />
      <div class="lista">
        <MyTarefa v-for="(tarefa, index) in tarefas  " :key="index" :tarefa="tarefa" />
      </div>
      <MyBox v-if="listaEstaVazia">
        você não está muito produtivo
      </MyBox>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import BarraLateral from "./components/BarraLateral.vue";
import MyBox from "./components/MyBox.vue";

import MyFormulario from "./components/MyFormulario.vue";
import MyTarefa from "./components/MyTarefa.vue";
import ITarefa from "./interfaces/ITarefa";

export default defineComponent({
  name: "App",
  components: { BarraLateral, MyFormulario, MyTarefa, MyBox },
  data() {
    return {
      tarefas: [] as ITarefa[],
      modoEscuroAtivo: false
    };
  },

  computed: { 
    listaEstaVazia(): boolean {
      return this.tarefas.length === 0
    }
   },

  methods: {
    salvarTarefa(tarefa: ITarefa) {
      this.tarefas.push(tarefa)
    },

    trocarTema(props:boolean) {

      this.modoEscuroAtivo = props

    }
  },
});
</script>


<style >
.lista {
  padding: 1.25rem;
}

main { 
  --bg-primario: #fff;
  --texto-primario: #000;
}

main.modo-escuro {
  --bg-primario: #2b2d42;
  --texto-primario: #ddd;
}

.conteudo{
  background-color: var(--bg-primario);
}
</style>
