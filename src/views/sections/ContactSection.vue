<template>
  <section id="contact_section">
    <div class="section section-contacts">
      <div class="container">
        <div class="md-layout">
          <div class="md-layout-item md-size-66 md-xsmall-size-100 mx-auto">
            <h2 class="text-center title">Dudas? Escríbenos! 📝</h2>
            <h4
              :style="{ fontSize: '1.125rem' }"
              class="text-center description"
            >
              Pedidos, dudas o comentarios. Nosotros te contactaremos.
            </h4>

            <form
              class="contact-form p-4"
              data-netlify="true"
              data-netlify-honeypot="bot-field"
              method="POST"
              name="contact-form"
            >
              <input name="form-name" type="hidden" value="contact-form" />

              <div class="md-layout">
                <div class="md-layout-item md-size-50 md-small-size-100">
                  <md-field>
                    <label>Tu nombre</label>
                    <md-input name="name" type="text" v-model="name"></md-input>
                  </md-field>
                </div>
                <div class="md-layout-item md-size-50 md-small-size-100">
                  <md-field>
                    <label>Tu email</label>
                    <md-input
                      name="email"
                      type="email"
                      v-model="email"
                    ></md-input>
                  </md-field>
                </div>
              </div>
              <md-field maxlength="5">
                <label>Tu mensaje</label>
                <md-textarea name="message" v-model="message"></md-textarea>
              </md-field>

              <br />

              <div class="md-layout">
                <div class="md-layout-item mx-auto text-center">
                  <md-button class="md-success" type="submit"
                    >Enviar mensaje</md-button
                  >
                </div>
              </div>
            </form>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      email: null,
      message: null,
      name: null
    };
  }
};
</script>

<style lang="scss">
.contact-form {
  padding-left: 2rem;
  padding-right: 2rem;
}
</style>
