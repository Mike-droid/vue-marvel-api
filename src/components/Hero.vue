<template>
  <div class="hero">
    <h2>{{ hero.name }}</h2>
    <img :src="`${hero.thumbnail.path}.${hero.thumbnail.extension}`" :alt="hero.name">
  </div>
</template>

<script>
export default {
  props: {
    hero: {
      name: String,
      thumbnail: String
    }
  }
}
</script>

<style lang="scss" scoped>
  .hero {
    border: 1px solid #000;
    width: 200px;
    height: 200px;

    & img {
      width: 80px;
      height: 80px;
    }
  }
</style>