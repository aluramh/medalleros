<template>
  <section class="section section-download" id="information">
    <!-- Background -->
    <div class="blurred_background" />

    <!-- Content -->
    <div class="container">
      <div class="md-layout text-center">
        <div class="md-layout-item md-size-66 md-small-size-100 mx-auto">
          <h2 class="text-center title">Buscas un medallero? Contactanos!</h2>

          <h2>Pedidos al 8110445403</h2>
          <h4>
            Cabo Breton 4057
            Rincón de La Primavera 6o Sector
            67174 Guadalupe, N.L.
          </h4>
          <p>
            Medalleros de acero con pintura horneada para exterior e interior
            <br />Entregas a domicilio
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {};
</script>

<style lang="scss">
$brightness: 55%;

#information {
  position: relative;
  overflow: hidden;
  background-color: red;

  .blurred_background {
    /* The image used */
    background-image: url("/images/backgrounds/contactUs.jpg");

    /* Add the blur effect */
    filter: blur(8px) brightness($brightness);
    -webkit-filter: blur(8px) brightness($brightness);

    /* Center and scale the image nicely */
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;

    /* 
    Full height and width.
    It is larger than the container to hide the blurred edges.
  */
    position: absolute;
    height: 110%;
    width: 110%;
    left: -5%;
    top: -5%;
  }
}
</style>

<style lang="scss" scoped>
#information {
  h2,
  h3,
  h4,
  p {
    color: rgb(230, 219, 219) !important;
  }
}
</style>