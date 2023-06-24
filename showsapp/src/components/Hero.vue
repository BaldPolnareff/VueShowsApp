<script setup>
    import { defineProps, defineEmits } from 'vue'
    const {isDragonball} = defineProps(['isDragonball'])
    const emit = defineEmits(['selectShow'])

    const emitSelectedShow = () => {
        emit('selectShow')
    }
</script>

<template>
    <div class="hero">
        <h1>{{ isDragonball ? 'Dragonball Z' : 'Rick and Morty'}}</h1>
        <p @click="emitSelectedShow">{{ isDragonball ? 'Rick and Morty' : 'Dragonball Z' }}</p>
    </div>
</template>

<style scoped>
    .hero {
        height : 40vh;
        display: flex;
        align-items: center;
        justify-content: center;
        position: relative;
        flex-direction: column;
        margin-bottom: 50px;
    }
    .hero img {
        position: absolute;
        height: 700px;
        opacity: 0.1;
    }
    .hero h1 {
        font-size: 100px;
        font-weight: bold;
    }
    .hero p {
        font-size: 20px;
        cursor: pointer;
    }
</style>