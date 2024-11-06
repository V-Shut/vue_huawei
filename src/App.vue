<script>
export default {
  data() {
    return {
      quote: {},
      error: false,
      loading: true,
      activeList: false,
      historyList: [],
      copyMessageVisible: false,
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
        this.historyList.push(data[0])
      } catch (error) {
        console.error('Fetch error:', error)
        this.loading = false
        this.error = true
      }
    },

    async copyQuote() {
      const textToCopy = this.quote.quote
      try {
        await navigator.clipboard.writeText(textToCopy)
        this.copyMessageVisible = true
        setTimeout(() => {
          this.copyMessageVisible = false
        }, 2000)
      } catch (err) {
        console.error('Failed to copy text:', err)
      }
    },

    toggleList() {
      this.activeList = !this.activeList
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
        <h1 class="quote" @click="copyQuote">{{ quote.quote }}</h1>
        <div class="container">
          <button class="more" @click="fetchQuote">More</button>
          <button class="copy-btn" @click="copyQuote" v-if="!copyMessageVisible">Copy</button>
          <span class="copy-message" v-else>Copied!</span>
          <p class="author">-{{ quote.author }}</p>
        </div>
      </template>
    </template>
    <div v-else class="error">
      Something went wrong...<br />
      Please, try again later or refresh your page
    </div>
    <div class="history" :class="{ open: activeList }">
      <button class="open_list" @click="toggleList">Open</button>
      <div class="elements">
        <li class="element" v-for="(obj, index) in historyList" :key="index" @click="quote = obj">
          {{ obj.quote }}
        </li>
      </div>
    </div>
  </div>
</template>
