<template>
  <nav class="bg-purple-600 text-white p-6 flex justify-between">
    <h1 class="text-xl font-bold">Anime Cards (Andres Pizana)</h1>
    <div>
      <router-link to="/" class="mr-4 hover:underline">Home</router-link>
      <router-link to="/login" class="hover:underline">Login</router-link>
    </div>
  </nav>
</template>

<style scoped>
.router-link-active {
  font-weight: bold;
  text-decoration: underline;
}
</style>

