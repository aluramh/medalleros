<template>
  <md-toolbar
    :class="extraNavClasses"
    :color-on-scroll="colorOnScroll"
    class="md-transparent md-absolute"
    id="toolbar"
    md-elevation="0"
  >
    <div class="md-toolbar-row md-collapse-lateral">
      <div class="md-toolbar-section-start">
        <h3 class="md-title">
          <LogoImage
            sourceImage="/images/otros/logo.png"
            :style="visibilityStyle"
          />
        </h3>
      </div>
      <div class="md-toolbar-section-end">
        <md-button
          :class="{ toggled: toggledClass }"
          @click="toggleNavbarMobile()"
          class="md-just-icon md-simple md-toolbar-toggle"
        >
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
        </md-button>

        <div class="md-collapse">
          <div class="md-collapse-wrapper">
            <mobile-menu nav-mobile-section-start="false">
              <!-- Here you can add your items from the section-start of your toolbar -->
            </mobile-menu>

            <md-list>
              <md-list-item href="#galeria" @click="toggleNavbarMobile()">
                <i class="material-icons">image</i>
                <p>Galeria</p>
              </md-list-item>

              <md-list-item href="#information" @click="toggleNavbarMobile()">
                <i class="material-icons">phone</i>
                <p>Contacto</p>
              </md-list-item>

              <!-- <md-list-item href="#" target="_blank">
                <i class="fab fa-twitter"></i>
                <p class="hidden-lg">Twitter</p>
                <md-tooltip md-direction="bottom">Follow us on Twitter</md-tooltip>
              </md-list-item>-->

              <md-list-item
                href="https://www.facebook.com/medalleros.mx"
                target="_blank"
              >
                <i class="fab fa-facebook-square"></i>
                <p class="hidden-lg">Facebook</p>
                <md-tooltip md-direction="bottom"
                  >Buscanos en Facebook!</md-tooltip
                >
              </md-list-item>

              <!-- <md-list-item href="#" target="_blank">
                <i class="fab fa-instagram"></i>
                <p class="hidden-lg">Instagram</p>
                <md-tooltip md-direction="bottom">Follow us on Instagram</md-tooltip>
              </md-list-item>-->
            </md-list>
          </div>
        </div>
      </div>
    </div>
  </md-toolbar>
</template>

<script>
let resizeTimeout;
function resizeThrottler(actualResizeHandler) {
  // ignore resize events as long as an actualResizeHandler execution is in the queue
  if (!resizeTimeout) {
    resizeTimeout = setTimeout(() => {
      resizeTimeout = null;
      actualResizeHandler();

      // The actualResizeHandler will execute at a rate of 15fps
    }, 66);
  }
}

import MobileMenu from "@/layout/MobileMenu";
import LogoImage from "@/components/LogoImage";

export default {
  components: {
    MobileMenu,
    LogoImage
  },
  data() {
    return {
      extraNavClasses: "",
      toggledClass: false,
      showLogo: false
    };
  },
  props: {
    type: {
      type: String,
      default: "white",
      validator(value) {
        return [
          "white",
          "default",
          "primary",
          "danger",
          "success",
          "warning",
          "info"
        ].includes(value);
      }
    },
    colorOnScroll: {
      type: Number,
      default: 0
    }
  },
  methods: {
    scrollToGallery() {
      console.log("SCROLL TO GALLERY");
    },
    scrollToContact() {
      var el = document.getElementById("information");
      el.scrollIntoView();
      window.scrollTo(el);
      console.log("SCROLL TO CONTACT", el);
    },
    bodyClick() {
      let bodyClick = document.getElementById("bodyClick");

      if (bodyClick === null) {
        let body = document.querySelector("body");
        let elem = document.createElement("div");
        elem.setAttribute("id", "bodyClick");
        body.appendChild(elem);

        let bodyClick = document.getElementById("bodyClick");
        bodyClick.addEventListener("click", this.toggleNavbarMobile);
      } else {
        bodyClick.remove();
      }
    },
    toggleNavbarMobile() {
      this.NavbarStore.showNavbar = !this.NavbarStore.showNavbar;
      this.toggledClass = !this.toggledClass;
      this.bodyClick();
    },
    handleScroll() {
      let scrollValue =
        document.body.scrollTop || document.documentElement.scrollTop;
      let navbarColor = document.getElementById("toolbar");
      this.currentScrollValue = scrollValue;
      if (this.colorOnScroll > 0 && scrollValue > this.colorOnScroll) {
        this.extraNavClasses = `md-${this.type}`;
        navbarColor.classList.remove("md-transparent");
      } else {
        if (this.extraNavClasses) {
          this.extraNavClasses = "";
          navbarColor.classList.add("md-transparent");
        }
      }
    },
    scrollListener() {
      resizeThrottler(this.handleScroll);
    },
    scrollToElement() {
      let element_id = document.getElementById("downloadSection");
      if (element_id) {
        element_id.scrollIntoView({ block: "end", behavior: "smooth" });
      }
    }
  },
  computed: {
    visibilityStyle() {
      return this.showLogo ? { opacity: 1 } : { opacity: 0 };
    }
  },
  mounted() {
    document.addEventListener("scroll", this.scrollListener);
  },
  created() {
    this.$eventHub.$on("PAGE_HEADER_VISIBILITY_CHANGED", pageHeaderVisible => {
      this.showLogo = !pageHeaderVisible;
    });
  },
  beforeDestroy() {
    document.removeEventListener("scroll", this.scrollListener);
    this.$eventHub.$off("PAGE_HEADER_VISIBILITY_CHANGED");
  }
};
</script>
