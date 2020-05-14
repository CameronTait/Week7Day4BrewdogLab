<template>
  <div>
    <h1>Brewdog Beers</h1>
    <div class="main-container">
      <beers-list :beers='beers'></beers-list>
      <beer-detail :beer='selectedBeer'></beer-detail>      
    </div>
  </div>
</template>

<script>
import { eventBus } from "./main.js"
import BeersList from './components/BeersList.vue';
import BeerDetail from './components/BeerDetail.vue';
import ListItem from './components/ListItem.vue';

export default {
  name: "app",
  data(){
    return {
      beers: [],
      selectedBeer: null,
      favouriteBeers: []
    };

  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(res => res.json())
    .then(beers => this.beers = beers)

    eventBus.$on('beer-selected', (beer) => {
      this.selectedBeer = beer
    })

    eventBus.$on('favourite-beer-selected', (favouriteBeer) => {
      this.favouriteBeers.push(favouriteBeer)
    })


  },
  components: {
    "beers-list": BeersList,
    "beer-detail": BeerDetail
  }

}
</script>

<style>

</style>
