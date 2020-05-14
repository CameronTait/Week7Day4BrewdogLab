<template lang="html">
<div>
    <li v-on:click="handleClick">{{beer.name}}</li>
    <input type="button" value="Add to favourites" v-on:click="handleClickAddToFavourites">
</div>
</template> 

<script>
import { eventBus } from '../main.js';


export default {
    name: 'list-item',
    props: ['beer'],
    methods: {
        handleClick(){
            eventBus.$emit('beer-selected', this.beer)
        },
        handleClickAddToFavourites(){
            this.beer.favourite = true

        //    eventBus.$emit('favourite-beer-selected', this.beer) 
        }
    }
}
</script>