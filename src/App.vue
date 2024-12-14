<script setup>
import { RouterView } from 'vue-router'
import { ref, onMounted } from 'vue'

const tiles = ref([])

onMounted(() => {
  // Generate random grayscale values for each tile
  tiles.value = Array.from({ length: 1400 }, () => {
    const baseColor = 100
    const variance = Math.floor(Math.random() * 50) - 100
    return baseColor + variance
  })
})
</script>

<template>
  <div class="min-h-screen bg-gray-50 dark:bg-gray-900 relative">
    <!-- Pattern Background -->
    <!-- Try these different class combinations for different tile sizes: -->

    <!-- Extra Small Tiles (32px) -->
    <!-- <div class="fixed inset-0 grid grid-cols-[repeat(auto-fill,minmax(32px,1fr))] gap-0.5"> -->

    <div class="fixed inset-0 grid grid-cols-[repeat(auto-fill,minmax(48px,1fr))] gap-0.5">
      <div
        v-for="(gray, index) in tiles"
        :key="index"
        class="aspect-square transition-colors duration-1000"
        :style="{
          backgroundColor: `rgb(${gray + 100}, ${gray + 100}, ${gray + 100})`,
          opacity: '0.2',
        }"
      ></div>
    </div>

    <!-- Main Content -->
    <div class="relative">
      <RouterView />
    </div>

    <!-- Footer -->
    <footer class="relative text-center py-6 text-sm text-gray-500 dark:text-gray-400">
      <p>© {{ new Date().getFullYear() }} EndStock. Market data for educational purposes only.</p>
    </footer>
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');

body {
  font-family: 'Inter', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

html {
  scroll-behavior: smooth;
}

* {
  -webkit-tap-highlight-color: transparent;
}
</style>
