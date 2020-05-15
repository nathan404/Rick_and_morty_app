<template>
  <div>
      <h1>Rick and Morty Episodes</h1>
          <episode-list :episodes="episodes"></episode-list>  
  </div>
</template>

<script>
import EpisodeList from './components/EpisodeList'

export default {
  name: 'app',
  data(){
    return {
      // episodes1: [],
      // episodes2: [],
      episodes: []
    }
  },
  components:{
    'episode-list': EpisodeList
  },
  methods: {
    getEpisodes: function(){
      const promises = [1, 2].map(num => {
        return fetch(
          `https://rickandmortyapi.com/api/episode/?page=${num}`
        ).then(res => res.json());
      });

      Promise.all(promises)
        .then(data => {
          const episodeData = data.reduce(
            (flat, toFlatten) => flat.concat(toFlatten.results),
            []
          );
          this.episodes = episodeData;
        })
    }
  },
  mounted(){
    this.getEpisodes();
  }
}
</script>

<style>
h1 {
  text-align: center;
  padding: 1rem;
}
</style>
