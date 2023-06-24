<script setup>
    import { ref, onMounted, watch } from 'vue'
    import axios from 'axios'
    import jsonData from '../data/dragon_ball_characters.json'
    import Card from './Card.vue'


    // Unofficial DBZ API, does not require a key //

    //?limit=8&offset=${page * 8}

    const page = ref(0)

    const characters = ref([])

    const getCharacters = () => {
        characters.value = jsonData.slice(page.value * 8, page.value * 8 + 8);
    }

    onMounted(() => {
        getCharacters()
    })

    watch(page, () => {
        getCharacters()
    })

    console.log(characters)


</script>

<template>
    <div class="container">
        <div class="cards">
            <Card
                v-for="character in characters"
                :key="character.id"
                :image="character.pic"
                :name="character.name"
                :race="character.race"
                :birthDate="character.birthDate"
            >
                <div class="race"><h4>{{ character.race }}</h4></div>
                <p>{{ character.birthDate }}</p>
            </Card>
            <div class="button-container">
                <button @click="page--">&lt</button>
                <button @click="page++">></button>
            </div>
        </div>
    </div>
</template>

<style scoped>
.container {
    background-color: rgb(27, 26, 26);
    padding: 30px
}
.cards {
    max-width: 1000px;
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
    height: 1200px
}
.cards h3 {
    font-weight: bold;
}
.cards p {
    font-size: 10px;
}
.jobs {
    display: flex;
    flex-wrap: wrap;
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
.spinner {
    display: flex;
    align-items: center;
    justify-content: center;
}
.race {
    display: flex;
    flex-wrap: wrap;
}

p {
    font-size: 12px;
}

h3 {
    font-size: 20px;
    font-weight: bold;
}
h4 {
    font-size: 16px;
    font-weight: bold;
}

</style>