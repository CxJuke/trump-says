<template>
  <div id="app">
    <header class="col-12 allign-items-center">
      <h1>Get a few daily trump quotes!</h1>
    </header>

    <main class="col-12">
      <trump-quote :quote="quote" />
    </main>
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
      quote: '',
      history: Array
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
#app {
  
}

header {
  text-align: center;
  margin-top: 20px;
  margin-bottom: 220px;
  
}

main {
  background-color: blueviolet;

}

footer {
  background-color: brown;
}
</style>
