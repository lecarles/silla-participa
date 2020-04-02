<template>
  <div class="footer">
    <div class="container footer-items">
      <div class="footer-logo">
        <img src="../assets/img/silla-ajuntament.gif" alt="Ajuntament de Silla">
      </div>
      <div class="footer-info">
        <p class="footer-title">
          Ajuntament de Silla
        </p>
        <p>Plaça del Poble 1, 46460 Silla - Apartat de correus 399. - Tel: 96 120 01 16 - Fax: 96 121 22 23</p>
        <p>Incidències i ajuda: <a href="mailto:incidencies@sillaparticipa.com">incidencies@sillaparticipa.com</a></p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AppFooter'
}
</script>

<style lang="scss" scoped>
@import '../sass/variables';

.footer {
  background: white;
  margin-top: 1rem;
  border-top: 1px solid $gray-400;

  &-title {
    font-weight: 600;
  }

  &-items {
    padding: 2.5rem 0;
    display: flex;
    align-items: center;

    img {
      width: 140px;
      margin-right: 2rem;
    }

    p {
      font-size: 1rem;
      margin: 0 ;
    }
  }
}

</style>
