<template lang="html">
  <div v-if='beer'>
    <br>
    <br>
    <h3 text-align="center"><u> {{ beer.name }} </u></h3>
    <p>Tagline: {{ beer.tagline }}</p>
    <p>Abv: {{ beer.abv }}</p>
    <p>Description: {{ beer.description }}</p>
    <br>
    <p>
    <img id="beer-bottle" :src="beer.image_url" height= 150px/>
    </p>
    <button v-on:click="AddToFavourite"><h3>Add Favourite Beer</h3></button>
    <br>
    <br>
    <button v-on:click="DeleteFavourite"><h3>Delete Favourite Beer</h3></button>
  </div>
</template>

<script>
import{eventBus} from '../main.js';

export default {
  name: 'beer-detail',
  props: ['beer'],
  methods:{
    AddToFavourite(){
      eventBus.$emit('favourite-beer', this.beer)
    },
    DeleteFavourite(){
      eventBus.$emit('delete-beer', this.beer)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
