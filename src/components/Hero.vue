<template>
  <div class="hero">
    <h2 class="heroName">{{ hero.name }}</h2>
    <img :src="`${hero.thumbnail.path}.${hero.thumbnail.extension}`" :alt="hero.name">
    <a :href="hero.urls[0].url" target="_blank">More info</a>
  </div>
</template>

<script>
export default {
  props: {
    hero: {
      name: String,
      thumbnail: String,
      moreInfoUrl: String,
    }
  }
}
</script>

<style lang="scss" scoped>
.hero {
  align-items: center;
  background: linear-gradient(90deg, rgba(241,134,63,1) 0%, rgba(231,103,60,1) 50%, rgba(216,55,55,1) 100%);
  background: rgb(241,134,63);
  border-radius: 10px;
  display: flex;
  flex-direction: column;
  height: 300px;
  justify-content: center;
  padding: 50px;
  width: 300px;

  & .heroName {
    color: rgb(10, 63, 163);
    font-size: 2em;
    font-weight: 700;
    margin-top: 20px;
  }

  & img {
    border-radius: 5px;
    height: 80%;
    width: 80%;
  }

  & a {
    background-color: blueviolet;
    border-radius: 5px;
    color: white;
    font-size: 1.2em;
    margin-bottom: 10px;
    margin-top: 10px;
    padding: 5px;
    text-decoration: none;
    &:hover {
      background-color: rgb(83, 0, 139);
    }
  }
}

</style>