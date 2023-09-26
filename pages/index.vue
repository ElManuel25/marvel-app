<template>
  <div class="characters-container">
    <CharacterCard v-for="character in characters" :key="character.id" :character="character"
      :show-details="showDetails" />
  </div>
</template>

<script>
import CharacterCard from '@/components/CharacterCard.vue';
import { ref } from 'vue';
import axios from "axios";

const Hash = '67d75cd3786a536d58e452fb82395b5e';
const publicKeys = 'ea871d53fc24840457d62779175612df';
const characters = ref([]);

const loadCharacters = async () => {
  const url = `https://gateway.marvel.com:443/v1/public/characters?limit=100&ts=1&apikey=${publicKeys}&hash=${Hash}`;
  const { data } = await axios.get(url);
  const charactersWithImages = data.data.results.filter(character => {
    return character.thumbnail.path !== "http://i.annihil.us/u/prod/marvel/i/mg/b/40/image_not_available";
  });
  characters.value = charactersWithImages;
}

const showDetails = (character) => {
  console.log('Mostrando detalles de:', character.name);
  // Puedes mostrar los detalles del personaje aquí
}

export default {
  components: {
    CharacterCard
  },
  setup() {
    loadCharacters();
    return {
      characters,
      showDetails
    };
  }
}
</script>

<style scoped>
.characters-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}
</style>