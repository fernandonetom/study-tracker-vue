<template>
  <Box>
    <div class="columns">
      <div class="column is-7">{{ task.taskName }}</div>
      <div class="column">
        <TimerDisplay :timeInSeconds="task.duration" />
      </div>
    </div>
  </Box>
</template>

<script lang="ts">
import type { PropType } from 'vue'
import TimerDisplay from './TimeDisplay.vue'
import Box from './Box.vue'
import type { ITask } from '@/interfaces/ITask'
export default {
  props: {
    task: {
      type: Object as PropType<ITask>,
      required: true  
    }
  },
  components: {
    TimerDisplay,
    Box
  }
}
</script>

<style scoped>
.box {
  background-color: #adb6bf;
}
</style>
