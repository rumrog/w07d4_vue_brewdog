<template>
    <li>{{beer.name}}</li>
</template>

<script>
import {eventBus} from '../main.js'
export default {
    name: 'list-component',
    props: ['beer']
}
</script>

<style>

</style>