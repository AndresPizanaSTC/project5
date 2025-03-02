<script setup>
import { ref, onMounted } from "vue";
import AnimeCard from "./components/AnimeCard.vue";

const animeList = ref([]);
const loading = ref(false);

const fetchAnime = async () => {
  loading.value = true;
  try {
    const response = await fetch("https://api.jikan.moe/v4/top/anime");
    const data = await response.json();
    animeList.value = data.data.map(anime => ({
      title: anime.title,
      description: anime.synopsis || "No description available.",
      image: anime.images.jpg.image_url,
      rating: anime.score || "N/A",
    }));
  } catch (error) {
    console.error("Error fetching anime:", error);
  } finally {
    loading.value = false;
  }
};

onMounted(fetchAnime);
</script>

<template>
  <div class="flex flex-col items-center p-6 bg-gray-100 min-h-screen">
    <h1 class="text-3xl font-bold text-purple-600 mb-6">Top Anime List</h1>
    <button @click="fetchAnime"
      class="bg-purple-600 hover:bg-purple-700 text-white px-4 py-2 rounded-md mb-6 transition">
      Refresh List
    </button>

    <p v-if="loading" class="text-lg text-gray-600">Loading...</p>

    <div v-else class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6">
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
