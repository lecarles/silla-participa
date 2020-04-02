<template>
  <b-navbar toggleable="md" type="light" fixed="top">
    <div class="container">
      <b-navbar-brand to="/">
        <img src="../assets/img/logo.png" alt="Silla Participa">
      </b-navbar-brand>
      <div class="ml-auto">
        <a
          v-if="$i18n.locale !== 'ca'"
          href="/"
          @click.prevent="localeChange('ca')"
        >
          Valencià
        </a>

        <a
          v-if="$i18n.locale !== 'es'"
          href="/es"
          @click.prevent="localeChange('es')"
        >
          Castellano
        </a>
      </div>
    </div>
  </b-navbar>
</template>

<script>
export default {
  name: 'AppNav',

  methods: {
    localeChange (newLocale) {
      this.$i18n.locale = newLocale
      const name = (newLocale === 'ca') ? this.$route.name.replace(/___es/g, '___ca') : this.$route.name.replace(/___ca/g, '___es')
      this.$router.push({ name })
    }
  }
}
</script>

<style lang="scss">
  @import '../sass/variables';

  .navbar-light {
    background: white;
    height: $navbar-height;
    width: auto;
    padding: 1rem;
    border-bottom: 1px mix($primary, $white, 50%) solid;

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
