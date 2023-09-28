<template>
    <div class="character-card">
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
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    padding: 20px;
    text-align: center;
    cursor: pointer;
    margin: 20px;
    border: 2px solid #ffd900;
    transition: transform 0.2s;
    box-shadow: 0 0 10px rgba(255, 255, 255, 0);

    transition: box-shadow 0.3s;
    filter: brightness(80%);

    transition: filter 0.3s;
    background-image: linear-gradient(45deg, #9f9f9f 25%, #9f9f9f 25%, #9f9f9f 50%, #888888 50%, #888888 75%, #9f9f9f 75%, #9f9f9f 100%);
    background-size: 200% 200%;
    transition: background-position 0.3s;
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
    font-size: 30px;
    font-weight: bold;
    color: #ffc107;

    border-bottom: 2px solid #ffc107;

    margin-bottom: 10px;

}

.character-description {
    font-size: 1.1em;
    color: #ff0000;
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
    color: #ffc107;
}

.first-three-series-title {
    font-size: 20px;

    border-bottom: 2px solid #ffc107;

    padding-bottom: 10px;

}

.first-three-series li {
    list-style-type: none;

    font-size: 18px;

}

.character-card:hover {
    transform: scale(1.05);
    cursor: pointer;
    box-shadow: 0 0 10px rgb(255, 1, 1);
    filter: brightness(100%);
    background-position: right bottom;
}

.character-card.clicked {
    transform: scale(1.1);
    border: 2px solid #333;
}
</style>
  