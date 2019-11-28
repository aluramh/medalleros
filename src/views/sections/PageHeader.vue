<template>
  <section id="main">
    <parallax class="page-header header-filter">
      <div class="md-layout page-header-content">
        <div class="md-layout-item">
          <div class="image-wrapper">
            <div class="brand">
              <div class="logo_container">
                <h1>
                  <img alt src="/images/otros/logo.png" srcset />
                  <!-- Medalleros -->
                </h1>
              </div>

              <br />

              <h3>Luce tus medallas!</h3>
            </div>
          </div>
        </div>
      </div>
    </parallax>
  </section>
</template>

<script>
export default {};
</script>

<style lang="scss">
#main {
  text-align: center;

  .page-header {
    &::before {
      background-image: url("/images/otros/main_background.jpeg");
      filter: brightness(50%);
      background-position: center;
    }
  }

  .logo_container {
    border-radius: 10px;
    background-color: white;
    padding: 1rem 1.2rem;
    margin: 1rem;
    box-shadow: 9px 10px rgb(233, 34, 34);
    // box-shadow: 0px 10px 25px rgba(0, 0, 0, 0.6);

    img {
      width: 80%;
    }
  }
}
</style>