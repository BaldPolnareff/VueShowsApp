<script setup>
  import { Comment, ref } from 'vue'
  import DragonballCards from './components/DragonballCards.vue';
  import RickAndMortyCards from './components/RickAndMortyCards.vue';
  import PracticeSlots from './components/PracticeSlots.vue';
  import Hero from './components/Hero.vue';
  import DragonBallCardsSuspense from './components/DragonBallCardsSuspense.vue';


  const isDragonball = ref(true)
</script>

<template>
  <main>
    <Hero 
      :isDragonball="isDragonball"
      @selectShow="isDragonball = !isDragonball"
    />
    <KeepAlive>
      <Component :is="isDragonball ? DragonBallCardsSuspense : RickAndMortyCards" />
    </KeepAlive>
  </main>
</template>

<style scoped>
  .cards spinner {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 700px;
    background-color: rgb(27, 26, 26);
  }
</style>
