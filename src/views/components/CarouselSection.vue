<template>
  <div class="wrapper">
    <div class="md-layout">
      <div class="md-layout-item md-size-75 mx-auto md-small-size-100">
        <md-card>
          <carousel
            :autoplay-timeout="5000"
            :mouse-drag="false"
            :per-page="1"
            :speed="700"
            :style="carouselStyle"
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

                <div @click="handleClick(image)" class="clickable">
                  <img
                    :height="height"
                    :src="image"
                    :style="{ height: `${height}px` }"
                    alt="carousel1"
                    class="cover"
                  >
                </div>
              </slide>
            </template>
          </carousel>
        </md-card>
      </div>
    </div>
  </div>
</template>

<script>
const carousel1 = require("@/assets/img/nature-2.jpg");
const carousel2 = require("@/assets/img/nature.jpg");
const carousel3 = require("@/assets/img/nature-3.jpg");

const height = 500;

export default {
  data() {
    return {
      height
    };
  },
  props: {
    images: {
      type: Array,
      default: () => [
        { image: carousel1, caption: "This is a caption" },
        { image: carousel2 },
        { image: carousel3 },
        { image: carousel1 },
        { image: carousel1 }
      ],
      required: true
    }
  },
  computed: {
    carouselStyle() {
      return { maxHeight: `${this.height}px` };
    }
  },
  methods: {
    handleClick(src) {
      this.$emit("imageClicked", src);
      console.log("CLICKED", src);
    }
  }
};
</script>

<style>
.cover {
  object-fit: cover;
}
.clickable {
  cursor: pointer;
}
</style>
