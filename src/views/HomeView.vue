<script setup>
import { ref } from 'vue'

const ticker = ref('')
const score = ref(75) // Example score, will be replaced with actual data later

const submitTicker = () => {
  // Will implement API call later
  console.log('Searching for:', ticker.value)
}
</script>

<template>
  <main class="min-h-[94vh] flex flex-col justify-center items-center px-8">
    <div
      class="w-full max-w-2xl mx-auto bg-white dark:bg-gray-800 rounded-2xl shadow-xl p-8 mt-8 mb-8"
    >
      <!-- Header -->
      <h1
        class="text-5xl font-bold mb-12 text-center bg-gradient-to-r from-blue-600 to-emerald-600 text-transparent bg-clip-text"
      >
        EndStock
      </h1>

      <!-- Search Section -->
      <div class="max-w-xl mx-auto">
        <label for="ticker" class="block text-sm font-medium mb-2 text-gray-700 dark:text-gray-200">
          Enter a stock ticker:
        </label>

        <div class="flex gap-2">
          <input
            id="ticker"
            v-model="ticker"
            type="text"
            class="flex-1 px-4 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent outline-none transition-all uppercase bg-gray-50 dark:bg-gray-700 dark:border-gray-600 dark:text-white"
            placeholder="e.g. AAPL"
            @keyup.enter="submitTicker"
          />
          <button
            @click="submitTicker"
            class="px-6 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition-colors"
          >
            Enter
          </button>
        </div>

        <!-- Score Display -->
        <div class="mt-12">
          <div class="relative h-4 bg-gray-200 dark:bg-gray-700 rounded-full overflow-hidden">
            <div
              class="absolute top-0 left-0 h-full bg-gradient-to-r from-red-500 via-yellow-500 to-green-500"
              style="width: 100%"
            />
            <div
              class="absolute top-0 h-full w-4 bg-white border-2 border-gray-400 rounded-full transition-all duration-500 shadow-lg"
              :style="{ left: `calc(${score}% - 0.5rem)` }"
            />
          </div>

          <!-- Score Legend -->
          <div class="mt-6 text-sm text-gray-600 dark:text-gray-300">
            <div class="flex justify-between">
              <span>Strong Sell</span>
              <span>Neutral</span>
              <span>Strong Buy</span>
            </div>
          </div>

          <!-- Score Explanation -->
          <p class="mt-8 text-gray-700 dark:text-gray-200 text-center">
            The EndStock score indicates the investment potential based on historical market data
            analysis. A higher score (closer to 100) suggests a stronger buy signal, while a lower
            score suggests a sell signal.
          </p>
        </div>
      </div>
    </div>
  </main>
</template>
