<template>
    <div>
      <!-- Nuevo select para elegir el personaje -->
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
        heroes: [], // Almacenará los personajes obtenidos de la API
        personajeSeleccionado: null
      };
    },
    methods: {
      async obtenerPersonajes() {
        const publicApiKey = 'ea871d53fc24840457d62779175612df';
        const hash = '67d75cd3786a536d58e452fb82395b5e';
        const characterIds = [1009351, 1009368, 1009220, 1009664, 1009610];
  
        const promises = characterIds.map(id => {
          const search_url = `https://gateway.marvel.com/v1/public/characters/${id}?ts=1&apikey=${publicApiKey}&hash=${hash}`;
          return axios.get(search_url);
        });
  
        try {
          const responses = await Promise.all(promises);
          this.heroes = responses.map(response => response.data.data.results[0]);
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
  