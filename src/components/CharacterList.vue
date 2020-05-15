<template>
  <div>
      <ol>
          <li v-for="(character, index) in characters" :key="index" :value="character">{{character.name}}</li>
      </ol>
  </div>
</template>

<script>
export default {
    name: 'character-list',
    props: ['characters']
}
</script>

<style>

</style>