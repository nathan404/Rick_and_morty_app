<template>
  <div>
      <li>
          {{character.name}}
          <button v-on:click="selectCharacter">Display Character Info</button>
          <button v-on:click="removeFav">Remove from Favourites</button>
      </li>
  </div>
</template>

<script>
import { eventBus } from '../main.js'

export default {
    name: 'fav-character-item',
    props: ["character"],
    methods: {
        selectCharacter: function(){
            eventBus.$emit("char-selected", this.character)
        },
        removeFav: function(){
            eventBus.$emit("fav-removed", this.character)
        }
    }
}
</script>

<style>

</style>