<template>
  <div id="app">
    <header class="col-12 allign-items-center">
      <h1>Get a your daily trump quotes!</h1>
    </header>

    <div class="col-6 mx-auto quote">
      <trump-quote :quote="quote" />
    </div>
    <div class="col-4 mx-auto history">
      <history-table :history="historyData" @get:newQuote="handleNewQuote"/>
    </div>
  </div>
</template>

<script>
import TrumpQuote from '@/components/TrumpQuote.vue'
import HistoryTable from '@/components/HistoryTable.vue'

export default {
  name: 'app',
  components: {
    TrumpQuote,
    HistoryTable
  },
  data() {
    return {
      quote: '',
      historyData: [
        {
          id: 1,
          quote: "quote1"
        },
        {
          id: 2,
          quote: "quote2"
        }

      ]
    }
  },
  mounted() {
    this.getQuote()
  },
  methods: {
    /**
     * async method gets a new trump quote from api
     */
    async getQuote() {
            try {
                const response = await fetch('https://api.whatdoestrumpthink.com/api/v1/quotes/random')
                const data = await response.json()
                this.quote = data.message
            } catch (error) {
                console.error(error)
            }
    },
    handleNewQuote() {
      console.log('getting new quote')
    }


  }
}
</script>

<style>
#app {
  
}

header {
  text-align: center;
  margin-top: 5vh;
  margin-bottom: 25vh;
  
}
.quote {

}

.history {
  margin-top: 25vh;
}



</style>
