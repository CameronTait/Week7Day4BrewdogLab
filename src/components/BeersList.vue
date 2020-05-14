<template lang="html">
<div>
  <input type="button" value="favourites beers" v-on:click="handleOnClickFavorites">
  <input type="button" value="All the beers" v-on:click="handleOnClickAll">
  <ul v-if="!favourites">
    <list-item v-for="(beer, index) in beers" :beer="beer" :key="index"></list-item>
  </ul>
  <ul v-if="favourites">
    <list-item v-if="beer.favourite" v-for="(beer, index) in beers" :beer="beer" :key="index"></list-item>
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
  },
  data() {
    return {
      favourites: false
    }
  },
  methods: {
    handleOnClickFavorites() {
      this.favourites = true
    },
    handleOnClickAll() {
      this.favourites = false
    }
  }
}
</script>

<style>

</style>
