<template>
    <v-col class="pr-3 pb-5" lg="4" sm="6"  md="4">
        <v-card shaped>
            <v-card-title class="blue draken-4 white--text headline">
                <strong>{{stock.name}} 
                    <small class="overline">
                        (Preço: {{stock.price}} | Qtde: {{stock.quantity}})
                        </small>
                </strong>
            </v-card-title>
            <v-card-text class="">
                Lorem ipsum dolor sit amet consectetur adipisicing elit.
            </v-card-text>
            <v-card-actions>
                <v-text-field label="Comprar ação" type="number" color="blue draken-4" v-model.number="quantity"/>
                <v-btn rounded class="mx-2" text color="blue draken-4" small 
                    @click="sellStock" :disabled="quantity <=0 || !Number.isInteger(quantity)">
                    <v-icon>mdi-logout-variant</v-icon>
                    <span class="">vender</span>
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
        sellStock () {
            const order = {
                stockId: this.stock.id,
                stockPrice: this.stock.price,
                quantity: this.quantity
            }
            this.$store.dispatch('sellStock', order)
            this.quantity = 0
        }
    }
}
</script>