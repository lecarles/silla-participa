<template>
  <b-navbar toggleable="md" type="light" fixed="top">
    <b-navbar-brand to="/">
      <img src="../assets/logo.png" alt="Silla Participa">
    </b-navbar-brand>
    <div class="ml-auto">
      <nuxt-link
        v-if="$i18n.locale !== 'ca'"
        :to="switchLocalePath('ca')"
      >
        Valencià
      </nuxt-link>

      <nuxt-link
        v-if="$i18n.locale !== 'es'"
        :to="switchLocalePath('es')"
      >
        Español
      </nuxt-link>
    </div>
  </b-navbar>
</template>

<script>
export default {
  name: 'AppNav'
}
</script>

<style lang="scss">
  @import '../sass/variables';

  .navbar-light {
    background: white;
    height: $navbar-height;
    width: auto;
    padding: 1rem;
    border-bottom: 1px solid $gray-400;

    .navbar-nav {
      a.nav-link {
        font-size: 1.25rem;
        color: $dark;

        &::after {
          display: none;
        }
      }
    }

    .navbar-brand {
      img {
        height: 2rem;
      }

      &::after {
        display: none;
      }

      &:hover {
        .lt {
          fill: $dark;
        }
      }
    }
  }
</style>
