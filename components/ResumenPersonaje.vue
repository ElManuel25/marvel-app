<template>
    <div v-if="personaje">
      <h2>{{ personaje.name }}</h2>
      <img :src="personaje.thumbnail.path + '.' + personaje.thumbnail.extension" alt="Personaje" />
      <p>{{ personaje.description }}</p>
      <p>Cómics: {{ personaje.comics.available }}</p>
      <p>Series: {{ personaje.series.available }}</p>
      <p>Stories: {{ personaje.stories.available }}</p>
      <p>Events: {{ personaje.events.available }}</p>
      <p>Primeras tres series:</p>
      <ul>
        <li v-for="(serie, index) in personaje.series.items.slice(0, 3)" :key="index">{{ serie.name }}</li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      personaje: Object
    }
  }
  </script>
  
  <style scoped>
  /* Estilos según tu preferencia */
  </style>
  