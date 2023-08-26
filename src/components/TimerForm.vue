<template>
    <div class="box">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
                <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?" v-model="description" />
            </div>
            <div class="column">
                <TimerControl @on-timer-is-ending="endTask" />
            </div>
        </div>
    </div>
</template>
  
<script lang="ts">
import { defineComponent } from "vue";
import TimerControl from "./TimerControl.vue";

export default defineComponent({
    name: "TimerForm",
    components: {
        TimerControl
    },
    data() {
        return {
            description: ''
        };
    },
    methods: {
        endTask(elapsedTime: Number): void {
            console.log('Tempo decorrido na tarefa: ', elapsedTime);
            console.log('Descrição da tarefa: ', this.description);
            this.description = '';
        }
    }
});
</script>