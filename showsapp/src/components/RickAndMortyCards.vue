<script setup>
    import { ref, onMounted, watch } from 'vue'
    import axios from 'axios'
    import jsonData from '../data/dragon_ball_characters.json'
    import Card from './Card.vue'


    // Official Rick and Morty API //

    //?limit=8&offset=${page * 8}

    const page = ref(1)

    const characters = ref([])

    const baseUrl = 'https://rickandmortyapi.com/api/character'


    onMounted(async () => {
        const response = await axios.get(baseUrl)
        characters.value = response.data.results
    })

    watch(page, async () => {
        const response = await axios.get(`${baseUrl}?page=${page.value}`)
        characters.value = response.data.results
    })



</script>

<template>
    <div class="container">
        <div v-if="characters" class="cards">
            <Card
                v-for="character in characters"
                :key="character.id"
                :image="character.image"
                :name="character.name"
                :race="character.species"
                :location="character.location.name"
            >
                <div class="race"><h4>{{ character.species }}</h4></div>
                <p>{{ character.location.name }}</p>
            </Card>
            <div class="button-container">
                <button @click="page--">&lt</button>
                <button @click="page++">></button>
            </div>
        </div>
        <div v-else class="cards spinner">
            <NSpin size="large"></NSpin>
        </div>
    </div>
</template>

<style scoped>
/* Rick and Morty */

    .container {
        background-color: rgb(27, 26, 26);
        padding: 30px;
        margin-top: 100px;
        height: 2500px;
    }
    .cards {
        margin: 0 auto;
        display: flex;
        flex-wrap: wrap;
        border-radius: 2px;
    }
    .cards h3 {
        font-weight: bold;
    }
    .cards p {
        font-size: 10px;
    }

    .button-container {
        display: flex;
        justify-content: center;
        padding-top: 30px
    }
    .button-container button {
        border: none;
        width: 50px;
        height: 50px;
        border-radius: 100%;
        margin: 0 5px;
        cursor: pointer;
    }
</style>