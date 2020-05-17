<template>
  <div>
      <ol>
          <li v-for="(character, index) in characters" :key="index" :value="character" v-on:click="handleSelect(character)">{{character.name}}</li>
      </ol>
    <!-- <button v-if="!character.isFavourite" v-on:click="addFavourite">Add to Favourites</button> -->
    <!-- <button v-if="character.isFavourite" v-on:click="removeFavourite">Remove from Favourites</button> -->
  </div>
</template>

<script>
import { eventBus } from "../main.js"
// import CharListUnit from "@/components/CharListUnit"

export default {
    name: 'character-list',
    props: ['characters'],
    data(){
        return {
            // selectedChar: null,
            // favChars: []
        }
    },
    methods: {
        handleSelect(character){
            eventBus.$emit('char-selected', character)
        },
        // addFavourite: function(){
        //     eventBus.$emit("fav-added", this.character)
        // },
        // removeFavourite: function(){
        //     eventBus.$emit("fav-removed", this.character)
        // }
    }
}
</script>

<style>

</style>