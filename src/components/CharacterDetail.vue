<template>
  <div v-if="character">
      <p>Name: {{character.name}}
      <p>Status: {{character.status}}</p>
      <p>Location: {{character.location.name}}</p>
      <p>Episodes: {{character.episode}}</p>
      <img class="face" :src="character.image"/>
  </div>
</template>

<script>
import { eventBus } from "../main.js"

export default {
    name: 'character-detail',
    props: ['character'],
    data(){
        return {
            // selectedCharacter: null
        }
    }
    // mounted() {
    //     eventBus.$on("char-selected", character => {
    //         this.character = character;
    //     })
    // }
}
</script>

<style>

</style>