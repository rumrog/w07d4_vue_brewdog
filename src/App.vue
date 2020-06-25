<template lang="html">
  <div id="app" class="grid">
    <h1 id="header">BrewDog Beers</h1>
    <div>
      <beers :beers="favourites" class="flexbox"></beers>
    </div>
    <div>
      <beers :beers="beers" class="flexbox"></beers>
    </div>
    <div>
      <beer-detail :beer="selectedBeer"></beer-detail>
    </div>
  </div>
</template>

<script>
import {eventBus} from './main.js'
import BeerDetail from './components/BeerDetail.vue'
import Beers from './components/Beers.vue'
import ListComponent from './components/ListComponent.vue'

export default {
  name: 'App',
  data(){
    return {
      beers: [],
      selectedBeer: null
    }
  },
  components: {
    "beers": Beers,
    "beer-detail": BeerDetail
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(res => res.json())
    .then(beers => {
      beers.forEach((beer) => {
        beer.favourite = false
      })
      this.beers = beers
      })

    eventBus.$on('beer-selected', (beer) => {
      this.selectedBeer = beer
    })
  },
  computed: {
    favourites: function() {
      return this.beers.filter(beer => {
        beer.favourite
      })
    }
  }
}
</script>

<style lang="css">
#app {
  background-color: aliceblue;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.grid {
  display: grid;
  grid-template-columns: 7fr 3fr;
}

.flexbox {
  display: flex;
}

li {
  list-style-type: none;
}

#header {
  grid-column: 1/3;
}
</style>
