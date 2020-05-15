<template>
  <div>
      <ol>
          <li v-for="(character, index) in characters" :key="index" :value="character" v-on:click="handleSelect(character)">{{character.name}}</li>
      </ol>
  </div>
</template>

<script>
import { eventBus } from "../main.js"

export default {
    name: 'character-list',
    // data(){
    //     return {
    //         selectedCharacter: null
    //     }
    // },
    props: ['characters'],
    methods: {
        handleSelect(selectedCharacter){
            eventBus.$emit('char-selected', selectedCharacter)
        }
    }
}
</script>

<style>

</style>