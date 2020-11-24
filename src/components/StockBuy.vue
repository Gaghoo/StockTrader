<template>
    <v-col class="pr-3 pb-5" lg="4" sm="6"  md="4">
        <v-card shaped>
            <v-card-title class="green draken-4 white--text headline">
                <strong>{{stock.name}} 
                    <small class="">(Preço: {{stock.price | currency}})</small>
                </strong>
            </v-card-title>
            <v-card-text class="">
                Lorem ipsum dolor sit amet consectetur adipisicing elit.
            </v-card-text>
            <v-card-actions>
                <v-text-field
                    label="Comprar ação"
                    type="number"
                    color="green draken-4"
                    v-model.number="quantity"
                    :error="insufficientFunds || quantity < 0 || !Number.isInteger(quantity)"
                    v-on:keyup.enter="buyStock"
                />
                <v-btn 
                    rounded class="mx-2" 
                    text color="green draken-4" 
                    small 
                    @click="buyStock" 
                    :disabled="insufficientFunds || quantity <=0 || !Number.isInteger(quantity)"
                >
                    <v-icon>mdi-login-variant</v-icon>
                    <span>{{insufficientFunds ? 'Insuficiente' : 'Comprar'}}</span>
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
    },
    computed:{
        funds(){
            return this.$store.getters.funds
        },
        insufficientFunds(){
            return this.quantity * this.stock.price > this.funds
        }
    }
}
</script>