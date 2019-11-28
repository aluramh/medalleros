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

<style>
.logo_image > img {
  max-width: 200px !important;
}
</style>