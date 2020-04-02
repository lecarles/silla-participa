<template>
  <div class="submitting">
    <client-only>
      <Lottie
        class-name="house-icon"
        renderer="svg"
        :loop="true"
        :autoplay="true"
        :animation-data="houseIcon"
      />
    </client-only>
    <p>{{ $t('form.submitting') }}</p>
  </div>
</template>

<script>
import Lottie from 'vue-lottie-web'
import houseIcon from '../assets/lottie/house.json'

export default {
  components: {
    Lottie
  },

  data () {
    return {
      houseIcon
    }
  }
}
</script>

<style lang="scss">
@import '../sass/variables';

.submitting {
  display: flex;
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  z-index: 1;
  background: rgba(255, 255, 255, .75);
  color: $gray-800;
  align-items: center;
  justify-content: center;
  flex-direction: column;

  .house-icon {
    width: 80px;
  }

  p {
    font-size: 2rem;
    font-weight: 600;
    margin-top: 1rem;
    color: $primary;
  }

  path {
    stroke: $primary;
  }
}
</style>
