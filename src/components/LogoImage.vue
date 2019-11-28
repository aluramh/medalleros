<template>
  <div class="logo_image">
    <img :src="sourceImage" alt="Luce tus medallas!" height="20" />
  </div>
</template>

<script>
export default {
  props: {
    sourceImage: {
      type: String
    }
  }
};
</script>

<style lang="scss">
.logo_image {
  transition: opacity 200ms;

  & > img {
    max-width: 200px !important;
  }
}
</style>
