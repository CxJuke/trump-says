<template>
  <div id="app">
    <header class="col-12 allign-items-center">
      <h1>Get your daily trump quotes!</h1>
    </header>

    <div class="col-md-8 col-sm-10 col-lg-6 mx-auto quote">
      <trump-quote :quote="quote" @get:newQuote="handleNewQuote"/>
    </div>
    <div class="col-md-6 col-sm-8 mx-auto history">
      <history-table :historyData="historyData"/>
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
      historyData: [],
      ready: true,
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
      this.ready = false
            try {
                const response = await fetch('https://api.whatdoestrumpthink.com/api/v1/quotes/random')
                const data = await response.json()
                this.quote = data.message
            } catch (error) {
                console.error(error)
            }
      this.ready = true
    },
    /**
     * Handles a new quote request
     */
    handleNewQuote(oldQuote) {
      if (this.ready){
      this.AddQuoteToHistory(oldQuote)

      this.getQuote();
      }
    },

    AddQuoteToHistory(oldQuote) {
      const id = this.historyData.length + 1;
      const newHistoryEntry = {
        id: id,
        quote: oldQuote,
      }
      

      this.historyData = [newHistoryEntry, ...this.historyData]
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
  min-height: 40vh;

}

.history {
  margin-top: 25vh;
}

#history-table {
    height: 15vh;
}


</style>
