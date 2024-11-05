<script>
import axios from 'axios'

export default {
  data() {
    return {
      quote: {},
      error: false,
      loading: true,
    }
  },

  methods: {
    async fetchQuote() {
      this.loading = true
      try {
        const response = await fetch('https://api.api-ninjas.com/v1/quotes', {
          method: 'GET',
          headers: {
            'X-Api-Key': 'o45M6E68HIpi/yBhHjXbzg==2WN4rgz5KuV0KUzO',
          },
        })

        if (!response.ok) {
          throw new Error('Network response was not ok')
        }

        const data = await response.json()
        this.quote = data[0]
        this.loading = false
      } catch (error) {
        console.error('Fetch error:', error)
        this.loading = false
        this.error = true
      }
    },
  },
  mounted() {
    this.fetchQuote()
  },
}
</script>

<template>
  <div class="app">
    <template v-if="!error">
      <div class="loading" v-if="loading">Loading...</div>
      <template v-else>
        <h1 class="quote">{{ quote.quote }}</h1>
        <div class="container">
          <button class="button" @click="fetchQuote">More</button>
          <p class="author">-{{ quote.author }}</p>
        </div>
      </template>
    </template>
    <div v-else class="error">
      Something went wrong...<br /> Please, try again later or refresh your page
    </div>
  </div>
</template>
