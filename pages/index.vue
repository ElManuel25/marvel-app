<template>
  <div class="search-container">
    <input v-model="searchTerm" placeholder="Search a character by name" class="search-input" />
  </div>
  <div class="characters-container">
    <CharacterCard v-for="character in filteredCharacters" :key="character.id" :character="character" :show-details="showDetails" />
  </div>
</template>

<script>
import CharacterCard from '@/components/CharacterCard.vue';
import { ref, computed, onMounted } from 'vue';
import axios from "axios";

const Hash = '67d75cd3786a536d58e452fb82395b5e';
const publicKeys = 'ea871d53fc24840457d62779175612df';
const characters = ref([]);
const originalCharacters = ref([]);
const searchTerm = ref('');

const loadCharacters = async (offset) => {
  const url = `https://gateway.marvel.com:443/v1/public/characters?limit=100&offset=${offset}&ts=1&apikey=${publicKeys}&hash=${Hash}`;
  const { data } = await axios.get(url);
  const charactersWithImages = data.data.results.filter(character => {
    return character.thumbnail.path !== "http://i.annihil.us/u/prod/marvel/i/mg/b/40/image_not_available";
  });
  characters.value = [...characters.value, ...charactersWithImages];
  originalCharacters.value = [...originalCharacters.value, ...charactersWithImages]; 
}

const showDetails = (character) => {
  console.log('Mostrando detalles de:', character.name);
}

const filterCharacters = () => {
  if (searchTerm.value.trim() === '') {
    characters.value = originalCharacters.value;
  } else {
    characters.value = originalCharacters.value.filter(character => {
      return character.name.toLowerCase().startsWith(searchTerm.value.toLowerCase());
    });
  }
}

const filteredCharacters = computed(() => {
  return characters.value.filter(character => {
    return character.name.toLowerCase().startsWith(searchTerm.value.toLowerCase());
  });
});

export default {
  components: {
    CharacterCard
  },
  setup() {
    onMounted(async () => {
      for (let i = 0; i < 17; i++) {
        await loadCharacters(i * 100);
      }
    });

    return {
      characters,
      showDetails,
      searchTerm,
      filterCharacters,
      filteredCharacters
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

.search-container {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 20px 0;
}

.search-input {
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 5px;
  width: 300px;
  background-color: azure;
}
</style>
