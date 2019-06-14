<template>
  <div class="wrapper">
    <div class="title">
      <h3>{{ title }}</h3>
    </div>

    <div class="md-layout">
      <div class="md-layout-item md-size-75 mx-auto md-small-size-100">
        <md-card>
          <carousel
            :autoplay-timeout="5000"
            :mouse-drag="false"
            :per-page="1"
            :speed="700"
            autoplay
            loop
            navigationEnabled
            navigationNextLabel="<i class='material-icons'>keyboard_arrow_right</i>"
            navigationPrevLabel="<i class='material-icons'>keyboard_arrow_left</i>"
          >
            <template v-for="({ image, caption }, i) in images">
              <slide :key="i">
                <div class="carousel-caption" v-if="caption">
                  <h4>{{ caption }}</h4>
                </div>

                <img :src="image" alt="carousel1" />
              </slide>
            </template>
          </carousel>
        </md-card>
      </div>
    </div>
  </div>
</template>

<script>
import { Modal } from "@/components";
const carousel1 = require("@/assets/img/nature-2.jpg");
const carousel2 = require("@/assets/img/nature.jpg");
const carousel3 = require("@/assets/img/nature-3.jpg");

export default {
  components: {
    Modal
  },
  data() {
    return {
      classicModal: false,
      selectedDate: new Date("2018/03/26")
    };
  },
  props: {
    title: {
      type: String,
      default: "Carousel"
    },
    images: {
      type: Array,
      default: () => [
        { image: carousel1, caption: "This is a caption" },
        { image: carousel2 },
        { image: carousel3 },
        { image: carousel1 },
        { image: carousel1 }
      ]
    }
  },
  methods: {
    classicModalHide() {
      this.classicModal = false;
    }
  }
};
</script>
