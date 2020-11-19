<template>
    <v-row>
        <StockSell v-for="(stock, index) in stocks" :key="index" :stock="stock"/>
    </v-row>
</template>


<script>
import {mapGetters} from 'vuex'
import StockSell from '@/components/StockSell'
export default {
    components:{
        StockSell
    },
    computed:{
        ...mapGetters({
            stocks: 'stockPortfolio'
        })
    }
}
</script>