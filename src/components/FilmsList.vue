<template lang="html">
<div id="filmList" class="filmList">
  <h2>Films</h2>
  <ul>
    <li v-on:click="handleClick(index)" v-for="(film, index) in films"> {{ film.title }} </li>
  </ul>
</div>
</template>

<script>
import { eventBus } from '../main.js';
export default {
  name: 'film-list',
  props: ['films'],
  methods: {
    handleClick(index) {
      eventBus.$emit('selected-film', this.films[index])
    }
  }
}
</script>

<style lang="css" scoped>

ul {
  list-style-type: none;
}

li {
  font-size: 1.2em;
  cursor: pointer;
  list-style-type: none;
}

li:hover {
  background-color: yellow;
}

.filmList {
  border: 2px solid red;
  border-radius: 15px;
  margin: 15px
}

</style>
