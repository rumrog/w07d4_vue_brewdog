<template lang="html">
  <div class="selected-beer" v-if="beer !== null">
    <h4> {{beer.name}} </h4>
    <h5> {{beer.tagline}} </h5>
    <img :src="beer.image_url">
    <p> {{beer.description}} </p>
    <p>ABV: {{beer.abv}} %</p>
    <label for="favourite">Favourite this beer </label><input v-on:change="setFavourite" id="favourite" type="checkbox">
  </div>
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'beer-detail',
  props: ['beer'],
  methods: {
      setFavourite() {
          eventBus.$emit('set-favourite', this.beer)
      }
  }
}
</script>

<style lang="css">

.selected-beer {
  background-color: white;
  border: 3px;
  border-style: double;
}

.selected-beer img {
  max-height: 200px;
}

</style>
