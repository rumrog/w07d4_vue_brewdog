<template>
    <li v-on:click="handleClick">{{beer.name}}</li>
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

</style>