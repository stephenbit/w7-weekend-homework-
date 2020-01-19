<template lang="html">
  <div id="FavouriteFilms">
    <h2>Favourites</h2>
    <ul>
      <li v-for="favouriteFilm in favouriteFilms"> {{favouriteFilm.name}} </li>
      <p>test</p>
    </ul>
  </div>
</template>



<!-- <ul>
  <li v-on:click="handleClick(index)" v-for="(film, index) in films"> {{ film.title }} </li>
</ul> -->

<script>
import { eventBus } from '../main.js';
import app from '../App.vue';
export default {
  name: 'favourite-films',
  props: ['favouriteFilms']
  }



</script>

<style lang="css" scoped>
  h2 {
    font-size: 2em;
  }
</style>
