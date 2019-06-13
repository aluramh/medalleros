<template>
  <div class="wrapper">
    <div id="images">
      <div class="title">
        <h2>Images</h2>
      </div>
      <div class="md-layout">
        <div
          :class="{ 'text-center': responsive }"
          class="md-layout-item md-size-20 md-xsmall-size-100"
        >
          <h4>Rounded Image</h4>
          <img
            :class="{ 'responsive-image': responsive }"
            :src="image"
            alt="Rounded Image"
            class="rounded"
          >
        </div>
        <div
          :class="{ 'text-center': responsive }"
          class="md-layout-item md-size-20 md-xsmall-size-100 ml-auto"
        >
          <h4>Circle Image</h4>
          <img
            :class="{ 'responsive-image': responsive }"
            :src="image"
            alt="Circle Image"
            class="rounded-circle"
          >
        </div>
        <div
          :class="{ 'text-center': responsive }"
          class="md-layout-item md-size-20 md-xsmall-size-100 ml-auto"
        >
          <h4>Rounded Raised</h4>
          <img
            :class="{ 'responsive-image': responsive }"
            :src="image"
            alt="Raised Image"
            class="img-raised rounded"
          >
        </div>
        <div
          :class="{ 'text-center': responsive }"
          class="md-layout-item md-size-20 md-xsmall-size-100 ml-auto"
        >
          <h4>Circle Raised</h4>
          <img
            :class="{ 'responsive-image': responsive }"
            :src="image"
            alt="Thumbnail Image"
            class="img-raised rounded-circle"
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      image: require("@/assets/img/faces/avatar.jpg"),
      responsive: false
    };
  },
  methods: {
    onResponsiveInverted() {
      if (window.innerWidth < 600) {
        this.responsive = true;
      } else {
        this.responsive = false;
      }
    }
  },
  mounted() {
    this.onResponsiveInverted();
    window.addEventListener("resize", this.onResponsiveInverted);
  },
  beforeDestroy() {
    window.removeEventListener("resize", this.onResponsiveInverted);
  }
};
</script>

<style lang="css"></style>
