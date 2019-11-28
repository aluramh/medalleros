<template>
  <section class="section section-download" id="information">
    <!-- Background -->
    <div class="blurred_background" />

    <!-- Content -->
    <div class="container">
      <div class="md-layout text-center">
        <div class="md-layout-item md-size-66 md-small-size-100 mx-auto">
          <h2 class="text-center title">Buscas un medallero? Contáctanos!</h2>

          <h2>
            Pedidos al telefono
            <a :href="`tel:${phone}`">
              <span class="contact_link">{{ phone }}</span>
            </a>
          </h2>

          <h3>o</h3>

          <h2>
            <a :href="`mailto:${email}`" target="_blank">
              <span class="contact_link">{{ email }}</span>
            </a>
          </h2>
          <h4></h4>
          <p>
            Medalleros de acero con pintura horneada para exterior e interior.
            <br />Hacemos entregas a domicilio desde Contry la Silla.
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data: () => ({
    email: "medallerosmex@gmail.com",
    phone: "8119991614"
  })
};
</script>

<style lang="scss">
$brightness: 55%;
$white: rgb(230, 219, 219);

#information {
  position: relative;
  overflow: hidden;
  background-color: red;

  h2,
  h3,
  h4,
  p {
    color: $white !important;
  }

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

  .contact_link {
    // color: rgb(255, 40, 40);
    color: $white;
    text-decoration: underline;
    word-wrap: break-word;
  }
}
</style>
