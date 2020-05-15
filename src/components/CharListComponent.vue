<template>
  <li v-on:click="handleClick">{{character}}</li>
</template>

<script>
import { eventBus } from "../main.js"

export default {
    name: 'char-list-component',
    props: ['character'],
    methods: {
        handleClick(){
            eventBus.$emit('character-selected', this.character)
        }
    }
}
</script>

<style>

</style>