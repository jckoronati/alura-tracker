<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
        <TimerDefault :seconds="seconds" />
        <button class="button" @click="start" :disabled="isCounting">
            <span class="icon">
                <i class="fas fa-play"></i>
            </span>
            <span>play</span>
        </button>
        <button class="button" @click="end" :disabled="!isCounting">
            <span class="icon">
                <i class="fas fa-stop"></i>
            </span>
            <span>stop</span>
        </button>
    </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TimerDefault from "./TimerDefault.vue";

export default defineComponent({
    name: "TimerControl",
    components: {
        TimerDefault
    },
    emits: ['onTimerIsEnding'],
    data() {
        return {
            seconds: 0,
            timer: 0,
            isCounting: false,            
        }
    },    
    methods: {
        start() {
            this.isCounting = true;
            this.timer = setInterval(() => {
                this.seconds += 1
            }, 1000);
        },
        end() {
            clearInterval(this.timer);
            this.isCounting = false;
            this.$emit('onTimerIsEnding', this.seconds);
            this.seconds = 0;
        }
    }
});
</script>