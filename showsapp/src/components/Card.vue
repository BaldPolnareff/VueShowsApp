<script setup>
    import { defineProps } from 'vue';

    const {image, name} = defineProps([
        'image', 
        'name', 
    ])
</script>

<template>
    <n-card>
        <template #cover>
            <img alt="example" :src="image"/>
        </template>
        <h3>{{ name }}</h3>
        <slot></slot>
    </n-card>
</template>

<style scoped>
.n-card {
    width: 200px;
    height: 450px;
    background-color: whitesmoke;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    border-radius: 2px;

}
.n-card img {
    background-color: black;
    display: flex;
    justify-content: center;
    align-items: center;
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

.race {
    display: flex;
    flex-wrap: wrap;
}
</style>