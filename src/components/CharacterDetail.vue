<template>
  <div v-if="character">
      <p>Status: {{character.status}}</p>
  </div>
</template>

<script>
import { eventBus } from "../main.js"

export default {
    name: 'character-detail',
    data(){
        return {
            character: null
        }
    },
    mounted() {
        eventBus.$on("char-selected", character => {
            // console.log(this.character, character)
            this.character = character;
        })
    }
}
</script>

<style>

</style>