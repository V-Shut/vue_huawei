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
      try {
        const response = await axios.get('https://favqs.com/api/qotd')
        this.quote = response.data.quote
        console.log(this.quote)
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
      <div class="quote" v-if="loading">Loading...</div>
      <template v-else>
        <h1 class="quote">{{ quote }}</h1>
        <p class="author">-{{ quote.author }}</p>
      </template>
    </template>
    <div v-else class="error">
      Something went wrong... Please, try again later or refresh your page
    </div>
  </div>
</template>
