<template>
  <div>
      <ul>
          <!-- <li v-for="(episode, index) in episodes" :key="index" :value="episode">{{episode.name}}</li> -->
      </ul>
  </div>
</template>

<script>
export default {
    name: 'episode-list',
    props: ['episodes']
}
</script>

<style>

</style>