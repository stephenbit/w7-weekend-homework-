<template lang="html">

  <div id="filmDetails" class="filmDetails">
    <h2>{{ selectedFilm.title }}
      <b>
        ({{ selectedFilm.release_date }})
      </b>
    </h2>
    <!-- <img src="src/assets/rt_score_logo.png">  <p>{{ selectedFilm.rt_score }}</p> -->
    <p>Directed by {{ selectedFilm.director }}</p>
    <p>Produced by {{ selectedFilm.producer }}</p>
    <p>{{ selectedFilm.description }}</p>
    <button v-on:click="addToFavourites" type="button" name="Add to favourites">Add to favourites</button>
  </div>

</template>

<script>
import { eventBus } from '../main.js';

export default {
  name: 'film-details',
  props: ['selected-film'],
  methods: {
    addToFavourites() {
      eventBus.$emit('favourite-films', this.selectedFilm)
    },
  }
}

</script>

<style lang="css" scoped>

.button {
  cursor: pointer;
}

.filmDetails {
  border: 2px solid red;
  border-radius: 15px;
  margin: 15px;
}

</style>
