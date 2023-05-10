<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <div>
      <div class="text-center mx-auto container py-10 rounded-md" role="group">
        <nav>
          <RouterLink class="mr-1 px-4 py-2 text-sm font-medium text-gray-900 active:text-pink-700 bg-white border border-gray-200 rounded-lg hover:bg-gray-100 focus:z-10 focus:ring-2 focus:ring-pink-700 focus:text-pink-700" to="/">Beranda </RouterLink>
          <RouterLink class="px-4 py-2 text-sm font-medium text-gray-900 active:text-pink-700 bg-white border border-gray-200 rounded-lg hover:bg-gray-100 hover:text-pink-700 focus:z-10 focus:ring-2 focus:ring-pink-700 focus:text-pink-700" to="/app">App Saya</RouterLink>
        </nav>
      </div>
    <RouterView />
  </div>
</template>

<style scoped>
nav a.router-link-exact-active {
  color: white;
  background: #db2777;
}
</style>
