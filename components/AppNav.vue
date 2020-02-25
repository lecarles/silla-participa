<template>
  <b-navbar toggleable="md" type="light" fixed="top">
    <b-navbar-brand to="/">
      <img src="../assets/logo.png" alt="Silla Participa">
    </b-navbar-brand>
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
    background: $light;
    border-bottom: 2px $primary solid;
    height: $navbar-height;
    width: auto;
    padding: 1rem;

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
