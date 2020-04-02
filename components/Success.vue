<template>
  <section class="success">
    <div class="icon-container">
      <client-only>
        <Lottie
          class-name="check-icon"
          renderer="svg"
          :loop="false"
          :autoplay="true"
          :animation-data="checkIcon"
        />
      </client-only>
    </div>
    <h2 class="m-0">
      {{ $t('success.heading') }}
    </h2>
    <p class="my-4">
      {{ $t('success.text') }}
    </p>
    <p>
      <a href="https://silla.es" class="btn btn-outline-primary">
        {{ $t('success.cta') }}
      </a>
    </p>
  </section>
</template>

<script>
import Lottie from 'vue-lottie-web'
import checkIcon from '../assets/lottie/check.json'

export default {
  components: {
    Lottie
  },

  data () {
    return {
      checkIcon
    }
  }
}
</script>

<style lang="scss">
  @import '../sass/variables';

  .icon-container {
    width: 150px;
    height: 150px;
    margin: 2rem auto;

    svg > g > g > g > path {
      fill: $secondary;
    }
  }

  .success {
    min-height: calc(100vh - 205px);
    padding: 2rem;
    text-align: center;
    display: flex;
    place-content: center;
    flex-direction: column;

    h2 {
      font-size: 2.5rem;
    }

    p {
      font-size: 1.25rem;
    }
  }
</style>
