<template lang="html">
  <div id="FavouriteFilms" class="favouriteFilms">
    <h2>Favourites</h2>
    <ul>
      <li v-on:click="removeFromFavourites(favouriteFilm)" v-for="favouriteFilm in favouriteFilms">{{favouriteFilm.title}} 🗑️</li>
    </ul>
  </div>
</template>

<script>
import { eventBus } from '../main.js';
import app from '../App.vue';
export default {
  name: 'favourite-films',
  props: ['favouriteFilms'],
  methods: {
    removeFromFavourites(film) {
      eventBus.$emit('remove-favourite', film)
    },
  }
}



</script>

<style lang="css" scoped>
  h2 {
    font-size: 1.2em;
  }

  ul {
    list-style-type: none;
  }

  li {
    list-style-type: none;
    cursor: pointer;
  }

  li:a {
    text-decoration: none;
  }

  .favouriteFilms {
    border: 2px solid red;
    border-radius: 15px;
    margin: 15px;
  }

</style>
