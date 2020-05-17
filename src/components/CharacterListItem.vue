<template>
  <div>
      <p>{{character.name}}</p>
      <button v-on:click="displayDetail">More info</button>
      <button v-if="!favChars.includes(selectedChar)" v-on:click="addFav">Add to Favourite Characters</button>
      <button v-if="favChars.includes(selectedChar)" v-on:click="removeFav">Remove from Favourite Characters</button>
  </div>
</template>

<script>
import { eventBus } from "./main.js"

export default {
    name: "character-list-item",
    props: ["character"],
    methods: {
        displayDetail: function() {
            eventBus.$emit("char-selected", this.character)
        },
        addFav: function(){
            eventBus.$emit("fav-added", this.character)
        },
        removeFav: function(){
            eventBus.$emit("fav-removed", this.character)
        }
    }
}
</script>

<style>

</style>