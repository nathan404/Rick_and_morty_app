<template>
  <div>
    <div class="main-container">
      <div class="characters">
      <h3>Rick and Morty Characters</h3>
          <character-list :characters="characters"></character-list>  
          <character-detail :character="selectedChar"></character-detail>
          <fav-character v-if="selectedChar" :favChars="favCharacters"></fav-character>
      </div>
      
      <div class="episodes">
        <h3>Episodes</h3>
          <episode-list :episodes="episodes"></episode-list>
      </div>
    </div>
  </div>
</template>

<script>
import { eventBus } from "./main.js"
import EpisodeList from './components/EpisodeList'
import CharacterList from './components/CharacterList'
import CharacterDetail from './components/CharacterDetail'
import FavCharacter from './components/FavCharacter'

export default {
  name: 'app',
  data(){
    return {
      episodes: [],
      characters: [],
      selectedChar: null,
      favCharacters: []
    }
  },
  components: {
    'episode-list': EpisodeList,
    'character-list': CharacterList,
    'character-detail': CharacterDetail,
    'fav-character': FavCharacter
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
      const charPromises = [25].map(num => {
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
    },

      addFavourite: function(character) {
        this.favCharacters.push(this.selectedChar)
      },

      removeFavourite: function(character) {
        this.favCharacters.splice(this.favCharacters.indexOf(this.character), 1)
      }
  },
  mounted(){
    this.getEpisodes();
    this.getCharacters();

    eventBus.$on("char-selected", character => (this.selectedChar = character));

    eventBus.$on("fav-added", character => this.addFavourite(character));

    eventBus.$on("fav-removed", character => this.removeFavourite(character));
  }
}
</script>

<style>
.main-container {
  display: flex;
  justify-content: space-between;
}
</style>
