<template lang="html">
  <div v-if="beer !== null">
    <h4> {{beer.name}} </h4>
  </div>
</template>

<script>
export default {
  name: 'beer-detail',
  props: ['beer']
}
</script>

<style lang="css">

</style>
