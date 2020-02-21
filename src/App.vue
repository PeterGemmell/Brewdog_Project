<template>
  <div>
    <h1 align="center"><u>Brewdog Beers</u></h1>
    <div class="main-container">
    <beer-select :beers='beers'></beer-select>
    <beer-detail :beer='selectedBeer'></beer-detail>
    <favourite-beers :favouritebeers='favouriteBeers'></favourite-beers>

    </div>
  </div>

</template>

<script>
import BeerSelect from './components/BeerSelect.vue';
import BeersList from './components/BeersList.vue';
import { eventBus } from './main.js';
import BeerDetail from './components/BeerDetail.vue';
import FavouriteBeers from './components/FavouriteBeers.vue';


export default {
  name: 'app',
  data(){
  return {
    beers: [],
    favouriteBeers: [],
    selectedBeer: null
  };
},
mounted(){
  fetch('https://api.punkapi.com/v2/beers')
  .then(res => res.json())
  .then(beers => this.beers = beers)

  eventBus.$on('beer-selected', (beer) => {
    this.selectedBeer = beer;
  }),
  eventBus.$on('favourite-beer', (beer) => {
  this.favouriteBeers.push(beer)
}),
  eventBus.$on('delete-beer', (beer) => {
    const beerIndex = this.favouriteBeers.indexOf(beer);
    this.favouriteBeers.splice(beerIndex, 1);
  })

},
components: {
  "beers-list": BeersList,
  "beer-detail": BeerDetail,
  "beer-select": BeerSelect,
  "favourite-beers": FavouriteBeers,
 }
}
</script>

<style>
.main-container {
  display: flex;
  justify-content: space-between;
  padding-left: 50px;
  padding-right: 230px;
  padding-top: 10px;
  border-top: solid;

}

#beerbottle {
  align-items: center;
}

</style>
