<template>
    <v-col class="pr-3 pb-5" lg="4" sm="6"  md="4">
        <v-card shaped>
            <v-card-title class="green draken-4 white--text headline">
                <strong>{{stock.name}} 
                    <small class="">(Preço: {{stock.price}})</small>
                </strong>
            </v-card-title>
            <v-card-text class="">
                Lorem ipsum dolor sit amet consectetur adipisicing elit.
            </v-card-text>
            <v-card-actions>
                <v-text-field label="Comprar ação" type="number" color="green draken-4" v-model.number="quantity"/>
                <v-btn rounded class="mx-2" text color="green draken-4" small 
                    @click="buyStock" :disabled="quantity <=0 || !Number.isInteger(quantity)">
                    <v-icon>mdi-login-variant</v-icon>
                    <span>comprar</span>
                </v-btn>
            </v-card-actions>
        </v-card>
    </v-col>
</template>


<script>
export default {
    props: ['stock'],
    data:()=>({
        quantity: 0
    }),
    methods:{
        buyStock () {
            const order = {
                stockId: this.stock.id,
                stockPrice: this.stock.price,
                quantity: this.quantity
            }
            this.$store.dispatch('buyStock', order)
            this.quantity = 0
        }
    }
}
</script>