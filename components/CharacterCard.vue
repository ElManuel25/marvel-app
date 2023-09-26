<template>
    <div class="character-card" @click="showDetails">
        <center>
            <div class="character-image-container">
                <img v-if="character.thumbnail" :src="character.thumbnail.path + '.' + character.thumbnail.extension" alt=""
                    class="character-image" />
            </div>
            <div class="character-name">{{ character.name }}</div>
            <p class="character-description">{{ character.description || "No description available" }}</p>
            <div class="character-stats">
                <div class="stat">
                    <h3>Comics</h3>
                    <p class="stat-value">{{ character.comics.available }}</p>
                </div>
                <div class="stat">
                    <h3>Series</h3>
                    <p class="stat-value">{{ character.series.available }}</p>
                </div>
                <div class="stat">
                    <h3>Stories</h3>
                    <p class="stat-value">{{ character.stories.available }}</p>
                </div>
                <div class="stat">
                    <h3>Events</h3>
                    <p class="stat-value">{{ character.events.available }}</p>
                </div>
            </div>
        </center>
        <h3 align="center" class="first-three-series-title">First three series:</h3>
        <ul class="first-three-series">
            <template v-if="character.series.items && character.series.items.length > 0">
                <li v-for="(seriesItem, index) in character.series.items.slice(0, 3)" :key="seriesItem.resourceURI">
                    {{ seriesItem.name }}
                </li>
            </template>
            <template v-else>
                <li>Not in any series</li>
            </template>
        </ul>
    </div>
</template>

  
<script>
import { ref } from 'vue';

const character = ref(null);
const isClicked = ref(false);

const showDetails = () => {
    console.log('Mostrando detalles de:', character.value.name);
    isClicked.value = !isClicked.value;
}

export { character, showDetails, isClicked };

export default {
    props: ['character'],
    setup() {
        const firstThreeSeries = ref([]);

        // Lógica para obtener las primeras tres series
        if (character.value && character.value.series && character.value.series.items) {
            firstThreeSeries.value = character.value.series.items.slice(0, 3);
        }

        return {
            firstThreeSeries,
            isClicked,
        };
    },
};
</script>
  
<style scoped>
.character-card {
    background-color: #fff;
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    padding: 20px;
    text-align: center;
    cursor: pointer;
    margin-bottom: 20px;
    border: 2px solid #333;
    transition: transform 0.2s;
}

.character-image-container {
    width: 100%;
    height: 300px;
    overflow: hidden;
    border-radius: 10px;
    margin-bottom: 10px;
}

.character-image {
    width: 100%;
    height: auto;
    border-radius: 10px;
}

.character-name {
    font-size: 1.5em;
    font-weight: bold;
    margin-bottom: 10px;
}

.character-description {
    font-size: 1.1em;
    color: #555;
    margin-bottom: 15px;
    text-align: justify;
}

.character-stats {
    display: flex;
    justify-content: center;
    margin-bottom: 20px;
}

.stat {
    margin-bottom: 20px;
    padding: 10px;
    background-color: #f0f0f0;
    border-radius: 10px;
}

.stat h3 {
    margin: 0;
    font-size: 20px;
    color: #333;
}

.stat-value {
    font-size: 24px;
    font-weight: bold;
    color: #e40f0f;
}

.first-three-series-title {
    font-size: 24px;
    font-weight: bold;
    margin-top: 20px;
    color: #333;
}

.first-three-series {
    list-style: none;
    padding: 0;
    font-size: 20px;
    color: #333;
}

.first-three-series li {
    margin-bottom: 10px;
    color: #680000;
}

.character-card:hover {
    transform: scale(1.05);
    cursor: pointer;
}

.character-card.clicked {
    transform: scale(1.1);
    border: 2px solid #333;
}
</style>
  