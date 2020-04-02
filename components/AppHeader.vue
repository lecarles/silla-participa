<template>
  <header>
    <div class="container">
      <div class="row">
        <div class="col-md-8 d-flex flex-column justify-self-stretch justify-content-center">
          <h1>Formulari 1</h1>
          <p>Subtitle</p>
        </div>
        <div class="col-md-4 d-none d-md-flex align-self-stretch justify-content-end">
          <img src="~assets/img/housing.svg" height="90" alt="">
        </div>
      </div>
    </div>
  </header>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
  @import '../sass/variables';

  header {
    color: $primary;
    padding: 2rem;
    background-color: lighten($primary, 40);
    border-bottom: 1px mix($primary, $white, 50%) solid;
  }

  h1 {
    font-weight: 900;
  }

  p {
    font-size: 1.25rem;
    margin-bottom: 0;
  }
</style>
