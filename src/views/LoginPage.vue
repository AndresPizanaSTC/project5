<script setup>
import { ref } from "vue";

const email = ref("");
const password = ref("");

const login = () => {
  alert(`Logging in with: ${email.value}, password: ${password.value}`);
};
</script>

<template>
  <div class="flex justify-center items-center min-h-screen bg-gray-100">
    <div class="bg-white p-8 shadow-md rounded-md w-96">
      <h2 class="text-2xl font-bold text-center mb-4">Login</h2>
      <form @submit.prevent="login">
        <div class="mb-4">
          <label class="block text-gray-700">Email</label>
          <input v-model="email" type="email" class="w-full p-2 border rounded-md">
        </div>
        <div class="mb-4">
          <label class="block text-gray-700">Password</label>
          <input v-model="password" type="password" class="w-full p-2 border rounded-md">
        </div>
        <button class="w-full bg-purple-600 hover:bg-purple-700 text-white p-2 rounded-md">
          Login
        </button>
      </form>
    </div>
  </div>
</template>
