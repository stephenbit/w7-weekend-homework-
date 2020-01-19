<template lang="html">
  <div class="app">
    <h1>Studio Ghibli Films</h1>
    <div class="content-container">
      <films-list :films='films'></films-list>
      <film-details v-if='selectedFilm' :selected-film='selectedFilm'></film-details>
      <favourite-films v-if='favouriteFilms' :favourite-films="favouriteFilms"></favourite-films>
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
    eventBus.$on('remove-favourite', (film) => {
      favouriteFilms.pop(film)
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

h1 {
  font-size: 4em;
  text-align: center;
}

.content-container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  border:
}

ul {
  list-style-type: none;
}

li {
  list-style-type: none;
}
</style>
