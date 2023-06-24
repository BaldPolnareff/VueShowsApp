<script setup>
  import { ref } from 'vue'
  import DragonballCards from './DragonballCards.vue';


  const isDragonball = ref(true)
</script>

<template>
    <Suspense>
        <template #default>
          <DragonballCards />
        </template>
        <template #fallback>
          <div class="cards">
            <NSpin size="large"></NSpin>
          </div>
        </template>
    </Suspense>
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