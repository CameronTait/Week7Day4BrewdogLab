<template lang="html">
  <div v-if='beer'> 
    <h3>{{beer.name}}</h3>
    <p><img :src="beer.image_url"></p>
    <p>Tag Line: {{beer.tagline}} </p>
    <p>ABV: {{beer.abv}} </p>
    <p v-if="beer.favourite">Favourite: {{beer.favourite}} </p>
    
  </div>
</template>

<script>


export default {
    name: 'beer-detail',
    props: ['beer']
}


</script>

<style>

</style> 