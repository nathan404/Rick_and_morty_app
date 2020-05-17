<template>
  <div>
      <ol>
          <li v-for="(character, index) in characters" :key="index" :value="character" v-on:click="handleSelect(character)">{{character.name}}</li>
            <!-- <char-listunit v-for="(character, index) in characters" :character="character" :key="index"></char-listunit> -->
      </ol>
  </div>
</template>

<script>
import { eventBus } from "../main.js"
// import CharListUnit from "@/components/CharListUnit"

export default {
    name: 'character-list',
    props: ['characters'],
    // components: {
    //     "char-listunit": CharListUnit
    // }
    // data(){
    //     return {
    //         selectedCharacter: null
    //     }
    // },
    methods: {
        handleSelect(selectedCharacter){
            eventBus.$emit('char-selected', selectedCharacter)
        }
    }
}
</script>

<style>

</style>