<template lang="html">
  <div class="selected-beer" v-if="beer !== null">
    <h4> {{beer.name}} </h4>
    <h5> {{beer.tagline}} </h5>
    <img :src="beer.image_url">
    <p> {{beer.description}} </p>
    <p>ABV: {{beer.abv}} %</p>
  </div>
</template>

<script>
export default {
  name: 'beer-detail',
  props: ['beer']
}
</script>

<style lang="css">

.selected-beer {
    border: 3px;
    border-style: double;
}

</style>
