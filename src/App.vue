<template>
  <main>
    <div class="columns is-gapless is-multiline">
      <div class="column is-one-quarter">
        <LateralMenu />
      </div>

      <div class="column is-three-quarter">
        <LearnForm @save-task="saveTask"/>
        <div class="list">
          <TaskList v-for="(task, index) in tasks" :key="index" :task="task"/>
          <Box v-if="empty">Get start studying some tech :)</Box>
        </div>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import LateralMenu from '@/components/LateralMenu.vue'
import LearnForm from '@/components/LearnForm.vue'
import TaskList from '@/components/TaskList.vue'
import Box from '@/components/Box.vue'
import {type ITask} from '@/interfaces/ITask'

export default {
  components: {
    LateralMenu,
    LearnForm,
    TaskList,
    Box
  },
  data(){
    return {
      tasks: [] as ITask[]
    }
  },
  computed: {
    empty():boolean {
      return this.tasks.length === 0
    }
  },
  methods: {
    saveTask(task: ITask){
      this.tasks.push(task)
    }
  }
}
</script>

<style scoped>
.list {
  padding: 1.5rem;
}
</style>