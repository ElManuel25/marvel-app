<template>
    <div class="character-card" @click="showDetails">
      <div class="character-image-container">
        <img
          v-if="character.thumbnail"
          :src="character.thumbnail.path + '.' + character.thumbnail.extension"
          alt=""
          class="character-image"
        />
      </div>
      <div class="character-name">
        {{ character.name }}
      </div>
    </div>
  </template>
  
  <script>
  import { ref } from 'vue';
  
  const character = ref(null);
  
  const showDetails = () => {
    console.log('Mostrando detalles de:', character.value.name);
    // Puedes mostrar los detalles del personaje aquí
  }
  
  export { character, showDetails };
  
  export default {
    props: ['character'],
  };
  </script>
  
  <style scoped>
  .character-card {
    background-color: #fff;
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    padding: 10px;
    text-align: center;
    cursor: pointer;
  }
  
  .character-image-container {
    width: 100px; /* Establece el ancho deseado para la imagen */
    height: 100px; /* Establece la altura deseada para la imagen */
    margin: 0 auto 10px;
    overflow: hidden;
    border-radius: 10px;
  }
  
  .character-image {
    width: 100%;
    height: auto;
  }
  
  .character-name {
    font-weight: bold;
  }
  </style>
  