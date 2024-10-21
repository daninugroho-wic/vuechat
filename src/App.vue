<template>
  <nav class="bg-blue-600 p-4">
    <div class="container mx-auto flex justify-between items-center">
      <div class="text-white text-lg font-bold">MyApp</div>
      <div class="space-x-4">
        <router-link to="/" class="text-white font-semibold hover:text-blue-300">Home</router-link>
        <router-link to="/chat" class="text-white font-semibold hover:text-blue-300">Chat</router-link>
        <router-link to="/dash" class="text-white font-semibold hover:text-blue-300">Dash</router-link>
        <router-link to="/login" class="text-white font-semibold hover:text-blue-300">Login</router-link>
        <router-link to="/page" class="text-white font-semibold hover:text-blue-300">Page</router-link>
      </div>
    </div>
  </nav>
  <router-view />
</template>

<style scoped>
/* Optional scoped CSS if needed */
</style>
