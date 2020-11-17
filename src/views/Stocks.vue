<template>
    <v-row>
        <StockBuy v-for="(stock, index) in stocks" :key="index" :stock="stock"/>
    </v-row>
</template>


<script>
import StockBuy from '../components/StockBuy'
export default {
    data:() => ({
        
    }),
    components:{
        StockBuy
    },
    computed:{
        stocks(){
            return this.$store.getters.stocks
        }
    }
}
</script>