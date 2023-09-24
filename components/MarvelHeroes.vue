<template>
    <div>
  

      <select v-model="personajeSeleccionado">
        <option v-for="hero in heroes" :key="hero.id" :value="hero">
          {{ hero.name }}
        </option>
      </select>
  
      <!-- Mostrar la imagen e información del personaje seleccionado -->
      <div v-if="personajeSeleccionado">
        <h2>{{ personajeSeleccionado.name }}</h2>
        <p>ID: {{ personajeSeleccionado.id }}</p>
        <img
          :src="personajeSeleccionado.thumbnail.path + '.' + personajeSeleccionado.thumbnail.extension"
          alt="Personaje"
        />
        <p>{{ personajeSeleccionado.description }}</p>
      </div>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        heroes: [], 
        personajeSeleccionado: null
      };
    },
    methods: {
      async obtenerPersonajes() {
        const publicApiKey = 'ea871d53fc24840457d62779175612df';
        const hash = '67d75cd3786a536d58e452fb82395b5e';

        const search_url = `https://gateway.marvel.com/v1/public/characters?nameStartsWith=Hulk&ts=1&apikey=${publicApiKey}&hash=${hash}`;
  
        try {
          const response = await axios.get(search_url);
          this.heroes = response.data.data.results;
        } catch (error) {
          console.error(error);
        }
      }
    },
    created() {
      this.obtenerPersonajes();
    }
  };
  </script>
  
  <style scoped>
  select {
    padding: 8px;
    font-size: 16px;
    border: 10px solid #f80c0c;
    border-radius: 4px;
  }
  </style>
  