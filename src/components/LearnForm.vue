<template>
  <div class="box">
    <div class="columns">
      <div class="column is-8" role="form" aria-label="Form to create a new learn">
        <input 
        type="text" 
        class="input" 
        placeholder="What subject are you studying?" 
        v-model="taskName"/>
      </div>
      <div class="column is-4">
        <TimerLearn @timer-stopped="finishTask" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import TimerLearn from './TimerLearn.vue'
import {type ITask} from '@/interfaces/ITask'

export default {
  components: {
    TimerLearn
  },
  emits: ['saveTask'],
  data() {
    return {
      taskName: ''
    }
  },
  methods: {
    finishTask(timeInSeconds: Number): void {
      this.$emit('saveTask', {
        duration: timeInSeconds,
        taskName: this.taskName
      } as ITask)
      this.taskName = ''
    }
  }
}
</script>
