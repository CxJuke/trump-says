<template>
  <div id="app">
    <trump-quote :quote="quote"/>
  </div>
</template>

<script>
import TrumpQuote from '@/components/TrumpQuote.vue'

export default {
  name: 'app',
  components: {
    TrumpQuote

  },
  data() {
    return {
      quote: ''
    }
  },
  mounted() {
    this.getNewQuote()
  },
  methods: {
    async getNewQuote() {
            try {
                const response = await fetch('https://api.whatdoestrumpthink.com/api/v1/quotes/random')
                const data = await response.json()
                this.quote = data.message
            } catch (error) {
                console.error(error)
            }
    }
  }
}
</script>

<style>

</style>
