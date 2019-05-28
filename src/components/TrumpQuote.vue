<template>
    <blockquote class="blockquote">
        <p class="mb-0">{{quote}}</p>
        <footer class="blockquote-footer"><font-awesome-icon icon="twitter" /> @realDonaldTrump</footer>
    </blockquote>

</template>

<script>
export default {
    name: 'trump-quote',
    props: {
        quote: '',
    },
}

</script>

<style scoped>

</style>
