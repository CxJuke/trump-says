<template>
    <div class="col-12 quote">
        <div>
        <blockquote class="blockquote">
            <p class="mb-0">{{quote}}</p>
            <footer class="blockquote-footer quote-name">Donald Trump</footer>
        </blockquote>
        </div>
        <quote-request @get:newQuote="handleNewQuote" @get:personalQuote="handlePersonalQuote"/>
    </div>

</template>

<script>
import QuoteRequest from '@/components/QuoteRequest.vue'

export default {
    name: 'trump-quote',
    props: {
        quote: '',
    },
    components: {
        QuoteRequest
    },
    methods: {
        handleNewQuote() {
            this.$emit('get:newQuote', this.quote)
        },
        handlePersonalQuote(nameContainer) {
            const container = nameContainer;
            container.quote = this.quote;

            this.$emit('get:personalQuote', container)
        }
    }
}

</script>

<style scoped>
.quote {
    text-align: center;
}
</style>
