<template>
  <div>
      <ol>
          <!-- <li v-for="(character, index) in characters" :key="index" :value="character" v-on:click="handleSelect(character)">{{character.name}}</li> -->
            <character-list-item v-for="(character, index) in characters" :character="character" :key="index"></character-list-item>
      </ol>
  </div>
</template>

<script>
// import { eventBus } from "../main.js"
import CharacterListItem from "./components/CharacterListItem"

export default {
    name: 'character-list',
    props: ['characters'],
    components: {
        "character-list-item": CharacterListItem
    }
    // data(){
    //     return {
    //         selectedCharacter: null
    //     }
    // },
    // props: ['characters'],
    // methods: {
    //     handleSelect(selectedCharacter){
    //         eventBus.$emit('char-selected', selectedCharacter)
    //     }
    // }
}
</script>

<style>

</style>