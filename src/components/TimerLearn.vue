<template>
  <div class="is-flex is-justify-content-space-between is-align-items-center">
    <TimeDisplay :timeInSeconds="timeInSeconds" />

    <button class="button" @click="start" :disabled="intervalId !== 0">
      <span class="icon">
        <i class="fas fa-play"></i>
      </span>
      <span>play</span>
    </button>
    <button class="button" @click="stop" :disabled="intervalId === 0">
      <span class="icon">
        <i class="fas fa-stop"></i>
      </span>
      <span>stop</span>
    </button>
  </div>
</template>

<script lang="ts">
import TimeDisplay from './TimeDisplay.vue'

export const timerStoppedEvent = 'TimerStopped'

export default {
  components: {
    TimeDisplay
  },
  emits: ['TimerStopped'],
  data() {
    return {
      timeInSeconds: 0,
      intervalId: 0
    }
  },
  computed: {
    timeDuration(): string {
      return new Date(this.timeInSeconds * 1000).toISOString().substring(11,19)
    }
  },
  methods: {
    start() {
      this.intervalId = setInterval(() => {
        this.timeInSeconds += 1;
      }, 10)
    },
    stop() {
      clearInterval(this.intervalId)
      this.intervalId = 0
      this.$emit(timerStoppedEvent, this.timeInSeconds)
      this.timeInSeconds = 0
    }
  }
}
</script>