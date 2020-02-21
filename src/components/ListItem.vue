<template lang="html">
  <div>
  <li v-on:click="handleClick">{{beer.name}}</li>
  <button v-on:click="handleClickFavourite"> Add To Favourites</button>
  </div>
</template>


<script>
import {eventBus} from '../main.js'

export default {
  name: 'list-item',
  props: ['beer'],


  methods: {
    handleClick: function() {
      eventBus.$emit('beer-selected', this.beer)
    },
    handleClickFavourite: function(){
      eventBus.$emit('favourite-beers', this.beer)
    }
  },
}
</script>

<style lang="css" scoped>
</style>
