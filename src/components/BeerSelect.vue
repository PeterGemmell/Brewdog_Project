<template lang="html">
  <form>
    <label for="beerSelect">Select A Beer</label>
    <select id="beerSelect" v-on:change="handleChange" v-model="beer">
      <option v-for="(beer, index) in beers" :value="beer" :key="index">{{beer.name}}</option>
    </select>
  </form>

</template>

<script>
import ListItem from './ListItem.vue';
import{eventBus} from '../main.js';

export default {
  name: 'beer-select',
  data(){
    return {
      beer: null
    }
  },
  props: ['beers'],
  methods: {
    handleChange() {
      eventBus.$emit('beer-selected', this.beer);
    }
  }
}
</script>

<style lang="css" scoped>
</style>
