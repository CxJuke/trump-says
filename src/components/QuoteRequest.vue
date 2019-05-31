<template>
    <div class="container mx-auto">
        <div v-if="checked">
            <input type="text" v-model="yourName" placeholder="Your Name"><button class="btn btn-primary" @click="handleNewPersonalRequest">Get a personal quote!</button>
        </div>
        <div v-else>
            <button class="btn btn-primary" @click="handleNewQuoteRequest">Get a new quote!</button>
        </div>
        <div id="personal-check">
            <input type="checkbox" id="checkbox" v-model="checked"><label id="personal-label">Personalized?</label>
        </div>
    </div>
</template>

<script>
export default {
    name: 'quote-request',
    data() {
        return {
            checked: false,
            yourName: ''
        }
    },
    methods: {
        handleNewQuoteRequest() {
            this.$emit('get:newQuote')
        },
        handleNewPersonalRequest() {
            this.$emit('get:personalQuote', {name: this.yourName, quote: ''})
        }
    }
    
}
</script>

<style scoped>
#personal-check {
    padding: 5px;
    text-align: center
}

#personal-check {

}
</style>
