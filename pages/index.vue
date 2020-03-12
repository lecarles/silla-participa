<template>
  <div>
    <info v-if="phase === 1" />
    <poll v-if="phase === 2" />
    <results v-if="phase === 3" />
  </div>
</template>

<script>
import Poll from '../components/Poll'
import Results from '../components/Results'
import Info from '../components/Info'

export default {
  components: {
    Info,
    Poll,
    Results
  },
  computed: {
    phase () {
      // const now = new Date()
      return 2
    }
  }
}
</script>

<style lang="scss">
@import '../sass/variables';
</style>
