<template>
  <div>
      <h1>Rick and Morty Characters</h1>
          <character-list :characters="characters"></character-list>  
          <character-detail />
      <h2>Episodes</h2>
          <episode-list :episodes="episodes"></episode-list>
  </div>
</template>

<script>
import EpisodeList from './components/EpisodeList'
import CharacterList from './components/CharacterList'
import CharacterDetail from './components/CharacterDetail'

export default {
  name: 'app',
  data(){
    return {
      episodes: [],
      characters: []
    }
  },
  components:{
    'episode-list': EpisodeList,
    'character-list': CharacterList,
    'character-detail': CharacterDetail
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
    },

    getCharacters: function(){
      // const charPromises = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30].map(num => {
      const charPromises = [1].map(num => {
        return fetch(
          `https://rickandmortyapi.com/api/character/?page=${num}`
        ).then(res => res.json());
      });

      Promise.all(charPromises)
        .then(data => {
          const charData = data.reduce(
            (flat, toFlatten) => flat.concat(toFlatten.results),
            []
          );
          this.characters = charData;
        })
    }
  },
  mounted(){
    this.getEpisodes();
    this.getCharacters();
  }
}
</script>

<style>
h1 {
  text-align: center;
  padding: 1rem;
}

</style>
