<template>
  <section>
    <strong>{{ timeDuration }}</strong>
  </section>
</template>

<script lang="ts">
export default {
  props: {
    timeInSeconds: {
      type: Number,
      default: 0
    }
  },
  computed: {
    timeDuration(): string {
      return new Date(Number(this.timeInSeconds) * 1000).toISOString().substring(11,19)
    }
  }
}
</script>