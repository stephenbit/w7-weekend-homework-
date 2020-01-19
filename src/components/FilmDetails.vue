<template lang="html">

  <div id="filmDetails">
      <h2>{{ selectedFilm.title }}
        <b>
          ({{ selectedFilm.release_date }})
        </b>
      </h2>
  </div>

</template>

<script>

export default {
  name: 'film-details',
  props: ['selected-film'],
  methods: {
    handleClick() {
      eventBus.$emit('favourite-film', this.selectedFilm)
    }
  }
}
</script>

<style lang="css" scoped>

h2 {
  font-size: 2em;
}

h2 b {
  font-size: 50%;
}
</style>
