<template lang="html">

<div>
  <h3><u>Favourite Beers</u></h3>
  <ul style="list-style-type:none;">
    <li v-for="(beer, index) in favouritebeers" :beer="beer" :key="index"><br><br>{{beer.name}}<br><img :src="beer.image_url" height= 50px/><hr></li>
  </ul>
</div>

</div>
</template>

<script>

export default {
  name: 'favourite-beers',
  props: ['favouritebeers']
}
</script>

<style lang="css" scoped>
</style>
