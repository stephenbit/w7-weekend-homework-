<template lang="html">
  <div id="FavouriteFilms">
    <h2>Favourites</h2>
    <ul>
      <li v-for="favouriteFilm in favouriteFilms"> {{favouriteFilm.title}} <a v-on:click="removeFromFavourites">🗑️</a></li>
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
    removeFromFavourites() {
      eventBus.$emit('remove-favourite', this.favouriteFilm)
    },
  }
}



</script>

<style lang="css" scoped>
  h2 {
    font-size: 2em;
  }

  ul {
    list-style-type: none;
  }

  li {
    list-style-type: none;
  }

  li:a {
    text-decoration: none;
  }

</style>
