<template>
  <div class="min-h-screen flex items-center justify-center bg-gray-900">
    <div class="bg-gray-800 p-8 rounded-lg shadow-lg max-w-sm w-full">
      <h2 class="text-2xl font-bold text-white text-center mb-6">Login</h2>
      <form @submit.prevent="handleLogin" class="space-y-4">
        <div class="inputBox">
          <label for="username" class="block text-sm font-medium text-gray-400">Username</label>
          <input v-model="username" type="text" id="username"
            class="mt-1 block w-full px-3 py-2 bg-gray-700 text-white rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
            required />
        </div>
        <div class="inputBox">
          <label for="password" class="block text-sm font-medium text-gray-400">Password</label>
          <input v-model="password" type="password" id="password"
            class="mt-1 block w-full px-3 py-2 bg-gray-700 text-white rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
            required />
        </div>
        <div class="flex justify-between text-sm text-gray-400">
          <a href="#" class="hover:underline">Forgot Password</a>
          <a href="#" class="hover:underline">Signup</a>
        </div>
        <button type="submit" class="w-full bg-indigo-500 text-white px-4 py-2 rounded-md hover:bg-indigo-600">
          Login
        </button>
      </form>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const username = ref("");
const password = ref("");

const handleLogin = () => {
  if (username.value && password.value) {
    localStorage.setItem("username", username.value);
    window.location.href = "/dash"; // Ganti ke halaman dashboard
  } else {
    alert("Please fill in all fields");
  }
};
</script>
