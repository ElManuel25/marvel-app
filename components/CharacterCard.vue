<template>
    <div class="character-card" @click="showDetails">
        <div class="character-image-container">
            <img v-if="character.thumbnail" :src="character.thumbnail.path + '.' + character.thumbnail.extension" alt=""
                class="character-image" />
        </div>
        <div class="character-name">
            {{ character.name }}
        </div>
    </div>
</template>
  
<script>
import { ref } from 'vue';

const character = ref(null);
const isClicked = ref(false);

const showDetails = () => {
  console.log('Mostrando detalles de:', character.value.name);
  isClicked.value = !isClicked.value; // Cambiamos el estado de clic
}

export { character, showDetails, isClicked };

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
    margin-bottom: 20px;
    border: 2px solid #333;
    margin-top: 20px;
    /* Añadido: separación del borde superior */
    margin-left: 20px;
    /* Añadido: separación del borde izquierdo */
    margin-right: 20px;
    /* Añadido: separación del borde derecho */
    transition: transform 0.2s;
}

.character-image-container {
    width: 300px;
    height: 300px;
    margin: 0 auto 10px;
    overflow: hidden;
    border-radius: 10px;
}

.character-image {
    width: 100%;
    height: auto;
    border-radius: 10px;
}

.character-name {
    font-weight: bold;
    color: #333;
}

.character-card:hover {
    transform: scale(1.05);
    /* Escalamos la tarjeta cuando el cursor está encima */
    cursor: pointer;
    /* Cambiamos el cursor a una mano para indicar que se puede hacer clic */
}

.character-card.clicked {
  transform: scale(1.1); /* Escalamos un poco más cuando se hace clic */
  border: 2px solid #333; /* Añadimos un borde oscuro cuando se hace clic */
}
</style>
  