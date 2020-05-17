<template>
    <div>
        <h3>Your favourite characters</h3>
            <div v-if="selectedChar">
                <p>Is this a favourite character? {{selectedChar.name}}</p>
                <button v-if="!favChars.includes(selectedChar)" v-on:click="addToFav">Add character to favourites</button>
                <p>Favourite characters list</p>
                <ul>
                    <li v-for="(character, index) in favChars" :character="character" :key="index">{{selectedChar}} <button v-on:click="removeFav(character)">Deselect {{character}}</button></li>
                </ul>
            </div>
    </div>
</template>

<script>
import { eventBus } from "../main.js"

export default {
    name: "fav-character",
    data(){
        return {
            selectedChar: {},
            favChars: []
        }
    },
    methods: {
        addToFav(){
            this.favChars.push(this.selectedChar)
        },
        removeFav(character){
            this.favChars.splice(this.favChars.indexOf(character), 1)
        }
    }
}
</script>

<style>

</style>