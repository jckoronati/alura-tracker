<template>
    <div class="box">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
                <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?" />
            </div>
            <div class="column">
                <div class="is-flex is-align-items-center is-justify-content-space-between">
                    <TimerDefault :seconds="seconds" />
                    <button class="button" @click="start">
                        <span class="icon">
                            <i class="fas fa-play"></i>
                        </span>
                        <span>play</span>
                    </button>
                    <button class="button" @click="end">
                        <span class="icon">
                            <i class="fas fa-stop"></i>
                        </span>
                        <span>stop</span>
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>
  
<script lang="ts">
import { defineComponent } from "vue";
import TimerDefault from "./TimerDefault.vue";

export default defineComponent({
    name: "TimerForm",
    components: {
        TimerDefault
    },
    data() {
        return {
            seconds: 0,
            timer: 0
        }
    },
    computed: {
        tempoDecorrido(): string {
            return new Date(this.seconds * 1000).toISOString().substring(11, 8)
        }
    },
    methods: {
        start() {
            this.timer = setInterval(() => {
                this.seconds += 1
            }, 1000)
        },
        end() {
            clearInterval(this.timer)
        }
    }
});
</script>