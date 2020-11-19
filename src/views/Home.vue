<template>
    <div>
        <h1 class="text-h2">Negocie e Consulte Suas Ações</h1>
        <v-sheet class="ma-2 pa-3" elevation="6" color="primary">
            <v-icon left color="white">mdi-information-outline</v-icon>
            <span class="text-capitalize white--text">você pode salvar & carregar dados</span>
        </v-sheet>
        <v-sheet class="ma-2 pa-3" elevation="6" color="success">
            <v-icon left color="white">mdi-information-outline</v-icon>
            <span class="text-capitalize white--text">Clique em 'finalizar o dia' para iniciar um novo dia</span>
        </v-sheet>
        <v-divider class="my-4"/>
        <p class="text-h4"><strong>Seu Saldo:</strong> {{funds}}</p>
    </div>
</template>


<script>
export default {
    computed:{
        funds(){
            return this.$store.getters.funds
        }
    }
}
</script>