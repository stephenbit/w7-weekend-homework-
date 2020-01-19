<template lang="html">
<div id="filmList">
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
</style>
