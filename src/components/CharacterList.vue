<template>
  <div>
      <ol>
          <li v-for="(character, index) in characters" :key="index" :value="character" v-on:click="handleSelect(character)">{{character.name}}</li>
      </ol>

            <!-- <h3>Your favourite characters</h3> -->
            <!-- <div v-if="selectedChar"> -->
                <!-- <p>Is this a favourite character? {{selectedChar}}</p>
                <button v-if="!favChars.includes(selectedChar)" v-on:click="addFavourite">Add character to favourites</button>
                <p>Favourite characters list</p>
                <ul>
                    <li v-for="(character, index) in favChars" :character="character" :key="index">
                        {{character.name}} 
                        <button v-on:click="removeFavourite(character)">Deselect {{character.name}}</button>
                    </li>
                </ul>
            </div> -->
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
        }
        // addFavourite(){
        //     eventBus.$emit("fav-added", this.selectedChar)
        // },
        // removeFavourite(character){
        //     eventBus.$emit("fav-removed", this.character)
        // }
    }
}
</script>

<style>

</style>