<template>
    <div>
      <div v-for="personaje in personajes" :key="personaje.id" class="personaje-card">
        <img :src="personaje.thumbnail.path + '.' + personaje.thumbnail.extension" alt="Personaje" />
        <p>{{ personaje.name }}</p>
        <button @click="seleccionarPersonaje(personaje)">Seleccionar</button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      personajes: Array,
      seleccionarPersonaje: Function
    }
  }
  </script>
  
  <style scoped>
  .personaje-card {
    border: 1px solid #ccc;
    padding: 10px;
    margin: 10px;
    text-align: center;
  }
  
  .personaje-card img {
    max-width: 100%;
  }
  
  .personaje-card button {
    margin-top: 10px;
  }
  </style>
  