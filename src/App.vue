<template lang="html">
  <div id="app" class="app">
    <h1>Studio Ghibli Films</h1>
    <h2>株式会社スタジオジブリ</h2>
    <div class="content-container">
      <films-list v-if='films.legnth!==0' :films='films'></films-list>
      <film-details v-if='selectedFilm' :selected-film='selectedFilm'></film-details>
      <favourite-films v-if='favouriteFilms.length!==0' :favourite-films="favouriteFilms"></favourite-films>
    </div>
</div>
</template>


<script>
import { eventBus } from './main.js';
import FilmsList from './components/FilmsList.vue';
import FilmDetails from './components/FilmDetails.vue';
import FavouriteFilms from './components/FavouriteFilms.vue';
export default {
  name: 'app',
  data(){
    return {
      films: [],
      selectedFilm: null,
      favouriteFilms: []
    }
  },
  mounted() {
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(response => response.json())
    .then(films => this.films = films)

    eventBus.$on('selected-film', (film) => {
      this.selectedFilm = film
    })
    eventBus.$on('favourite-films', (favouriteFilm) => {
      if (!this.favouriteFilms.includes(favouriteFilm)){
        this.favouriteFilms.push(favouriteFilm)
      }
    })
    eventBus.$on('remove-favourite', film => {
      this.favouriteFilms.pop(film)
    })
  },

  components: {
    "films-list": FilmsList,
    "film-details": FilmDetails,
    "favourite-films": FavouriteFilms
  }
}
</script>

<style lang="css" scoped>

.app {
  background-color: pink;
}

h1 {
  font-size: 4em;
  text-align: center;
}

h2 {
  font-size: 2em;
  text-align: center;
  padding-top: 1px;
}

.content-container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
}

ul {
  list-style-type: none;
}

li {
  list-style-type: none;
}
</style>
