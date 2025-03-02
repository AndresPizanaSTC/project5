<script setup>
import { ref } from "vue";
import { faker } from "@faker-js/faker";
import AnimeCard from "./components/AnimeCard.vue";

const animeList = ref([]);

const generateAnime = () => {
  animeList.value = Array.from({ length: 8 }, () => ({
    title: faker.commerce.productName(),
    description: faker.lorem.sentence(),
    image: `https://picsum.photos/200/300?random=${Math.random()}`,
    rating: (Math.random() * 5 + 5).toFixed(1),
  }));
};

generateAnime();
</script>

<template>
  <div class="flex flex-col items-center p-6 bg-gray-100 min-h-screen">
    <h1 class="text-3xl font-bold text-purple-600 mb-6">Random Anime Generator</h1>
    <button @click="generateAnime"
      class="bg-purple-600 hover:bg-purple-700 text-white px-4 py-2 rounded-md mb-6 transition">
      Generate More
    </button>
    <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6">
      <AnimeCard
        v-for="(anime, index) in animeList"
        :key="index"
        :title="anime.title"
        :description="anime.description"
        :image="anime.image"
        :rating="anime.rating"
      />
    </div>
  </div>
</template>
