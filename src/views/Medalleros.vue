<template>
  <div class="wrapper">
    <!-- Header -->
    <PageHeader />

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
                <h2 class="title text-center">Medallas 🥇</h2>
                <h5
                  class="description"
                >Dale un vistazo a nuestra seleccion de medalleros disponibles.</h5>
              </div>
            </div>

            <div class="md-layout">
              <div class="md-layout-item md-size-66 mx-auto text-center">
                <md-button :class="buttonClass(250)" @click="selectedPrice = 250">$250</md-button>

                <md-button
                  :class="buttonClass(300)"
                  :style="{ marginLeft: '1rem', marginRight: '1rem' }"
                  @click="selectedPrice = 300"
                >$300</md-button>

                <md-button :class="buttonClass(350)" @click="selectedPrice = 350">$350</md-button>
              </div>
            </div>
            <CarouselSection :images="imagesArray[selectedPrice]" @imageClicked="classicModalOpen" />
          </div>
        </div>
      </section>

      <!-- Gallery -->
      <section class="md-content" id="galeria">
        <div class="section">
          <div class="container">
            <div class="md-layout mx-auto">
              <div class="card-holder">
                <div class="md-layout-item md-size-90 md-xsmall-size-100 mx-auto">
                  <md-card
                    :key="image"
                    :style="cardStyle(image)"
                    @click.native="classicModalOpen(image)"
                    md-with-hover
                    v-for="{image} in imagesArray[selectedPrice]"
                  >
                    <md-card-content></md-card-content>
                  </md-card>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Modal -->
      <Modal @close="classicModalHide" v-if="classicModal">
        <template slot="header">
          <!-- <h4 class="modal-title">Modal Title</h4> -->
          <md-button
            @click="classicModalHide"
            class="md-simple md-just-icon md-round modal-default-button"
          >
            <md-icon>clear</md-icon>
          </md-button>
        </template>

        <template slot="body">
          <img :alt="modalImage" :src="modalImage" />
          <!-- <p>
            Far far away, behind the word mountains, far from the
            countries Vokalia and Consonan
          </p>-->
        </template>

        <template slot="footer">
          <md-button @click="classicModalHide" class="md-danger md-simple">Close</md-button>
        </template>
      </Modal>

      <!-- UI Components
      <div class="section section-javascript">
        <div class="container">
          <javascript-components></javascript-components>
        </div>
      </div>-->

      <!-- Information -->
      <InformationSection />

      <!-- Contacto -->
      <ContactSection />

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

              <!-- <md-button class="md-twitter">
                <i class="fab fa-twitter"></i>Tweet
              </md-button>-->
              <md-button class="md-facebook" href="https://www.facebook.com/medalleros.mx">
                <i class="fab fa-facebook-square"></i> Share
              </md-button>
              <!-- <md-button class="md-google">
                <i class="fab fa-google-plus"></i> Share
              </md-button>
              <md-button class="md-github">
                <i class="fab fa-github"></i> Star
              </md-button>-->
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
import imagesArray from "@/assets/js/images.js";
import { Modal } from "@/components";
// Sections
import ContactSection from "./sections/ContactSection";
import InformationSection from "./sections/InformationSection";
import PageHeader from "./sections/PageHeader";

export default {
  components: {
    Modal,
    CarouselSection,
    BasicElements,
    Navigation,
    SmallNavigation,
    Tabs,
    NavPills,
    Notifications,
    // TypographyImages,
    JavascriptComponents,
    LoginCard,
    ContactSection,
    InformationSection,
    PageHeader
  },
  bodyClass: "index-page",

  data() {
    return {
      modalImage: null,
      classicModal: false,
      selectedPrice: 300,
      imagesArray,
      name: null,
      email: null,
      message: null
    };
  },
  mounted() {
    this.modalImage = this.imagesArray[this.selectedPrice][0].image;
  },
  methods: {
    buttonClass(price) {
      return this.selectedPrice == price ? "md-primary" : "md-secondary";
    },
    cardStyle(src) {
      return {
        backgroundImage: src,
        background: `url(${src})`,
        backgroundRepeat: "no-repeat",
        backgroundSize: "cover",
        backgroundPosition: "center"
      };
    },
    classicModalHide() {
      this.classicModal = false;
    },
    classicModalOpen(src) {
      this.classicModal = true;
      this.modalImage = src;
    }
  }
};
</script>

<style lang="scss">
.card-holder {
  flex-flow: row;
  display: flex;

  .md-card,
  .md-card-media-cover {
    width: 150px;
    height: 150px;
    margin: 4px;
    display: inline-block;
    vertical-align: top;
  }
}

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
