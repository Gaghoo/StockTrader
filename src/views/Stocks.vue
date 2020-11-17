<template>
    <v-row>
        <StockBuy v-for="(stock, index) in stocks" :key="index" :stock="stock"/>
    </v-row>
</template>


<script>
import StockBuy from '../components/StockBuy'
export default {
    data:() => ({
        stocks: [
            {id: 1, name: 'Atacadão', price: 27},
            {id: 2, name: 'Inspire Academia', price: 58},
            {id: 3, name: 'Google', price: 207},
            {id: 4, name: 'BMW', price: 512},
            {id: 5, name: 'Mercado Livre', price: 270},
            {id: 6, name: 'Maia Construção', price: 36},
        ]
    }),
    components:{
        StockBuy
    }
}
</script>