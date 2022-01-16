<template>
  <div>
    <ul class="heroesWrapper">
      <li v-for="hero in heroes" :key="hero.name">
        <Hero :hero="hero" />
      </li>
    </ul>
  </div>
</template>

<script>
import { base_url } from "../api/marvelApi"
import Hero from "../components/Hero"

export default {
  data() {
    return {
      heroes: []
    }
  },

  mounted() {
    const getHeroes = async () => {
      const arrayHeroes = []
      try {
        const response = await fetch(`${base_url}:443/v1/public/characters?ts=1&apikey=${process.env.VUE_APP_API_KEY}&hash=${process.env.VUE_APP_HASH}`);
        const data = await response.json();
        data.data.results.forEach(hero => {
          arrayHeroes.push(hero)
        })
        console.log('array heroes:', arrayHeroes)
        return arrayHeroes
      }
      catch (error) {
        console.error(`Error en la petición: ${error}`);
      }
    }
    getHeroes().then(heroes => {
      this.heroes = heroes
    })
  },

  components: { Hero }
}

</script>

<style lang="scss" scoped>
  .heroesWrapper {
    list-style: none;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
  }
</style>