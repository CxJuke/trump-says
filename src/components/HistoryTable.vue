<template>
    <div id="history-table">
        <table class="table">
            <thead>
                <tr>
                    <th>Recent Quotes</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="quote in history" :key="quote.id">
                    <td>{{quote.quote}}</td>
                </tr>
            </tbody>
        </table>
    </div>
    
</template>

<script>
export default {
    name: 'history-table',
    props: {
        history: Array,
    },
}
</script>

<style>

</style>
