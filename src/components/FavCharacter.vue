<template>
    <div>
        <h3>Your favourite characters</h3>
                <p>Is this a favourite character? {{character}}</p>
                <button v-if="!favCharacters.includes(character)" v-on:click="addFavourite">Add character to favourites</button>
                <p>Favourite characters list</p>
                <ul>
                    <li v-for="(character, index) in favChars" :character="character" :key="index">
                        {{character.name}} 
                        <button v-on:click="removeFavourite">Deselect {{character.name}}</button>
                    </li>
                </ul>
    </div>
</template>

<script>
import { eventBus } from "../main.js"

export default {
    name: "fav-character",
    props: ['favChars'],
    data(){
        return {
            character: {},
            favCharacters: []
        }
    },
    methods: {
        addFavourite: function(){
            eventBus.$emit("fav-added", this.character)
        },
        removeFavourite: function(){
            eventBus.$emit("fav-removed", this.character)
        }
    }
}
</script>

<style>

</style>