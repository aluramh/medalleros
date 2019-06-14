<template>
  <div class="wrapper">
    <!-- Header -->
    <parallax :style="headerStyle" class="page-header header-filter">
      <div class="md-layout">
        <div class="md-layout-item">
          <div class="image-wrapper">
            <div class="brand">
              <h1>Medalleros</h1>
              <h3>Luce tus medallas</h3>
            </div>
          </div>
        </div>
      </div>
    </parallax>

    <div class="main main-raised">
      <!-- UI Components -->
      <!-- <div class="section section-basic">
        <div class="container">
          <div class="title">
            <h2>Basic Elements</h2>
          </div>
          <basic-elements></basic-elements>
        </div>
      </div>-->

      <!-- Misc images -->
      <!-- <div class="section">
        <div class="container">
          <typography-images></typography-images>
        </div>
      </div>-->

      <!-- Carousel -->
      <section id="carousel_section">
        <div class="section section-javascript">
          <div class="container">
            <div class="md-layout">
              <div class="md-layout-item md-size-66 md-xsmall-size-100 mx-auto text-center">
                <h2 class="title text-center">Medallas</h2>
                <h5
                  class="description"
                >Dale un vistazo a nuestra seleccion de medalleros disponibles.</h5>
              </div>
            </div>

            <div class="md-layout">
              <div class="md-layout-item md-size-66 mx-auto text-center">
                <md-button class="md-primary">$250</md-button>

                <md-button
                  :style="{ marginLeft: '1rem', marginRight: '1rem' }"
                  class="md-primary"
                >$300</md-button>
                <md-button class="md-primary">$350</md-button>
              </div>
            </div>

            <CarouselSection/>
          </div>
        </div>
      </section>

      <!-- UI Components
      <div class="section section-javascript">
        <div class="container">
          <javascript-components></javascript-components>
        </div>
      </div>-->

      <!-- Contacto -->
      <section id="contact_section">
        <div class="section section-contacts">
          <div class="container">
            <div class="md-layout">
              <div class="md-layout-item md-size-66 md-xsmall-size-100 mx-auto">
                <h2 class="text-center title">Contactanos!</h2>
                <!-- <h4 :style="{ fontSize: '1.125rem'}" class="text-center description">
                Divide details about your product or agency work into parts.
                Write a few lines about each one and contact us about any
                further collaboration. We will responde get back to you in a
                couple of hours.
                </h4>-->
                <form class="contact-form">
                  <div class="md-layout">
                    <div class="md-layout-item md-size-50">
                      <md-field>
                        <label>Your Name</label>
                        <md-input type="text" v-model="name"></md-input>
                      </md-field>
                    </div>
                    <div class="md-layout-item md-size-50">
                      <md-field>
                        <label>Your Email</label>
                        <md-input type="email" v-model="email"></md-input>
                      </md-field>
                    </div>
                  </div>
                  <md-field maxlength="5">
                    <label>Your Message</label>
                    <md-textarea v-model="message"></md-textarea>
                  </md-field>
                  <br>
                  <div class="md-layout">
                    <div class="md-layout-item md-size-33 mx-auto text-center">
                      <md-button class="md-success">Send Message</md-button>
                    </div>
                  </div>
                </form>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Social media -->
      <section id="socialmedia_section">
        <div class="section section-download" id="downloadSection">
          <div class="container">
            <div class="sharing-area text-center">
              <div class="md-layout">
                <div class="md-layout-item">
                  <h3>Siguenos</h3>
                </div>
              </div>

              <md-button class="md-twitter">
                <i class="fab fa-twitter"></i>Tweet
              </md-button>
              <md-button class="md-facebook">
                <i class="fab fa-facebook-square"></i> Share
              </md-button>
              <md-button class="md-google">
                <i class="fab fa-google-plus"></i> Share
              </md-button>
              <md-button class="md-github">
                <i class="fab fa-github"></i> Star
              </md-button>
            </div>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
import BasicElements from "./components/BasicElementsSection";
import Navigation from "./components/NavigationSection";
import SmallNavigation from "./components/SmallNavigationSection";
import Tabs from "./components/TabsSection";
import NavPills from "./components/NavPillsSection";
import Notifications from "./components/NotificationsSection";
// import TypographyImages from "./components/TypographyImagesSection";
import CarouselSection from "./components/CarouselSection";
import JavascriptComponents from "./components/JavascriptComponentsSection";
import { LoginCard } from "@/components";

export default {
  components: {
    CarouselSection,
    BasicElements,
    Navigation,
    SmallNavigation,
    Tabs,
    NavPills,
    Notifications,
    // TypographyImages,
    JavascriptComponents,
    LoginCard
  },
  bodyClass: "index-page",
  props: {
    image: {
      type: String,
      // default: require("@/assets/img/headerImage.jpg")
      default: require("../../public/images/medalleros200/IMG_1519.jpg")
    }
  },
  data() {
    return {
      firstname: null,
      email: null
    };
  },
  methods: {},
  computed: {
    headerStyle() {
      return {
        backgroundImage: `url(${this.image})`
      };
    }
  }
};
</script>

<style lang="scss">
.section-download {
  .md-button + .md-button {
    margin-left: 5px;
  }
}

@media all and (min-width: 991px) {
  .btn-container {
    display: flex;
  }
}
</style>
