<script setup>
defineProps(["title", "description", "image", "rating"]);
</script>

<template>
  <div class="bg-white rounded-lg shadow-md overflow-hidden p-4 text-center">
    <img :src="image" alt="Anime Image" class="w-full h-48 object-cover rounded-md">
    <h3 class="text-lg font-semibold mt-3">{{ title }}</h3>
    <p class="text-gray-600 text-sm mt-1">{{ description }}</p>
    <p class="text-yellow-500 font-bold text-lg mt-2">⭐ {{ rating }}</p>
  </div>
</template>
