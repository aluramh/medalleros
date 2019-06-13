<template>
  <div class="wrapper">
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
      <div class="section section-javascript">
        <div class="container">
          <javascript-components></javascript-components>
        </div>
      </div>

      <!-- Contacto -->
      <div class="section section-contacts">
        <div class="container">
          <div class="md-layout">
            <div class="md-layout-item md-size-66 md-xsmall-size-100 mx-auto">
              <h2 class="text-center title">Work with us</h2>
              <h4 class="text-center description">
                Divide details about your product or agency work into parts.
                Write a few lines about each one and contact us about any
                further collaboration. We will responde get back to you in a
                couple of hours.
              </h4>
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

      <!-- Social media -->
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
import JavascriptComponents from "./components/JavascriptComponentsSection";
import { LoginCard } from "@/components";

export default {
  components: {
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
  name: "index",
  bodyClass: "index-page",
  props: {
    image: {
      type: String,
      default: require("@/assets/images/fotosdevariosmedalleros/IMG_4178.jpg")
    },
    leaf4: {
      type: String,
      default: require("@/assets/img/leaf4.png")
    },
    leaf3: {
      type: String,
      default: require("@/assets/img/leaf3.png")
    },
    leaf2: {
      type: String,
      default: require("@/assets/img/leaf2.png")
    },
    leaf1: {
      type: String,
      default: require("@/assets/img/leaf1.png")
    },
    signup: {
      type: String,
      default: require("@/assets/img/city.jpg")
    },
    landing: {
      type: String,
      default: require("@/assets/img/landing.jpg")
    },
    profile: {
      type: String,
      default: require("@/assets/img/profile.jpg")
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
