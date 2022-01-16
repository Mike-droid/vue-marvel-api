<template>
  <div class="heroesDiv">
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
        const response = await fetch(`${base_url}ts=1&apikey=${process.env.VUE_APP_API_KEY}&hash=${process.env.VUE_APP_HASH}`);
        const data = await response.json();
        data.data.results.forEach(hero => {
          arrayHeroes.push(hero)
        })
        //console.log('array heroes:', arrayHeroes)
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
.heroesDiv {
  background: rgb(251,112,19);
  background: radial-gradient(circle, rgba(251,112,19,1) 0%, rgba(160,41,1,1) 29%, rgba(118,26,3,1) 49%, rgba(216,55,55,1) 100%);
  width: 100%;
}
.heroesWrapper {
  display: grid;
  gap: 20px;
  grid-template-columns: repeat(3, 1fr);
  justify-items: center;
  list-style: none;
  padding: 0;
  width: 100%;
}

@media screen and (max-width: 1350px) {
  .heroesWrapper {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media screen and (max-width: 920px) {
  .heroesWrapper {
    grid-template-columns: repeat(1, 1fr);
  }
}

@media screen and (max-width: 500px) {
  .hero {
    height: 200px;
    width: 80%;

    & .heroName {
      font-size: 1.5em;
    }
  }
}
</style>
