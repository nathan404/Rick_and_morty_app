<template>
  <div>
      <h3>Your favourite characters:</h3>
      <!-- <button v-if="!favChars.includes(character)" v-on:click="addToFav">Add character to favourites</button> -->
      <ul>
          <!-- <li v-for="(favChar, index) in favChars" :favChar="favChar" :key="index">{{favChar.name}} <button v-on:click="removeFav(char)">Deselect {{favChar.name}}</button></li> -->
          <fav-character-item v-for="(character, index) in favChars" :character="character" :key="index"></fav-character-item>
      </ul>
  </div>
</template>

<script>
import FavCharacterItem from "./components/FavCharacterItem"

export default {
    name: 'fav-character',
    props: ['favChars'],
    components: {
        "fav-character-item": FavCharacterItem
    }
    // methods: {
    //     addToFav(){
    //         this.favChars.push(this.character)
    //     },
    //     removeFav(character){
    //         this.favChars.splice(this.favChars.indexOf(character), 1)
    //     }
    // }
}
</script>

<style>

</style>