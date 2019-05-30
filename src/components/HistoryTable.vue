<template>
    <div id="history-table">
        <table class="table" id="table-header">
            <thead>
                <tr>
                    <th>Recent Quotes</th>
                </tr>
            </thead>
        </table>
        <div class="overflow-div">
            <table id="table-data" class="table table-condensed">
                <tbody>
                    <tr v-for="quote in historyData" :key="quote.id">
                        <td>{{quote.quote}}</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
    
</template>

<script>
export default {
    name: 'history-table',
    props: {
        historyData: Array,
    },
}
</script>

<style scoped>
.table {
    table-layout: fixed;
}

.overflow-div {
    overflow-y: auto;
}


</style>
