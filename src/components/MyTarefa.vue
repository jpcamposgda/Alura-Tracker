<template>
    <MyBox>
        <div class="columns">
            <div class="column is-7">
                {{tarefa.descricao || 'Tarefa sem descrição'}}
            </div>

            <div class="column">
                <MyCronometro :tempoEmSegundos="tarefa.duracaoEmSegundos"  />
            </div>
        </div>
    </MyBox>
</template>


<script lang="ts">
import ITarefa from '@/interfaces/ITarefa';
import { defineComponent, PropType } from 'vue'
import MyBox from './MyBox.vue'
import MyCronometro from './MyCronometro.vue';

export default defineComponent({
    name: 'MyTarefa',
    components: { MyCronometro, MyBox },
    props: { 
        tarefa: { 
            type: Object as PropType<ITarefa>,
            required: true
        }
    }
})
</script>



<style scoped>

.box {
    background: #FAF0CA;
}
</style>
