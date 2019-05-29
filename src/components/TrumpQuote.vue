<template>
    <div class="col-12 quote">
        <blockquote class="blockquote">
            <p class="mb-0">{{quote}}</p>
            <footer class="blockquote-footer quote-name">Donald Trump</footer>
        </blockquote>
        <button class="btn btn-primary" @click="handleNewQuoteRequest">Get a new quote!</button>
    </div>

</template>

<script>
export default {
    name: 'trump-quote',
    props: {
        quote: '',
    },
    methods: {
        handleNewQuoteRequest() {
            this.$emit('get:newQuote')
        }
    }
}

</script>

<style scoped>
.quote {
    text-align: center;
}
</style>
