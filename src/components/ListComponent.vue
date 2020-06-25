<template>
    <li v-on:click="handleClick"><h2>{{beer.name}}</h2> <br><img :src="beer.image_url"></li>
</template>

<script>
import {eventBus} from '../main.js'
export default {
    name: 'list-component',
    props: ['beer'],
    methods: {
        handleClick(){
            eventBus.$emit('beer-selected', this.beer)
        }
    }
}
</script>

<style>
li {
    justify-content: center;
    width: 15vw;
    padding: 5vw;
    margin: 10px;
    background-color: white;
    box-shadow: 10px 10px 10px hsla(0, 0%, 0%, 0.1);
    border-radius: 10px;
}

img {
    max-height: 100px;
}
</style>