<template lang="html">
  <div>
    <label><u>Select A Beer:</u></label>
    <br>
    <br>
    <br>
    <ul>
      <list-item v-for="(beer, index) in beers" :beer="beer" :key="index"></list-item>
    </ul>
  </div>

</template>

<script>
import ListItem from './ListItem.vue';

export default {
name: 'beers-list',
props: ['beers'],
components: {
  "list-item": ListItem
 }
}
</script>

<style lang="css" scoped>
</style>
