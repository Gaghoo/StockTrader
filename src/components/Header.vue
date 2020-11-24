<template>
    <nav>
        <v-app-bar app>
            <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
            <v-toolbar-title>
                <span class="vaiDaErrado font-weight-thin">Stock</span>
                <span class="vaiDaErrado vaiDaCerto">Trade</span>
            </v-toolbar-title>
            <v-spacer></v-spacer>
            <v-toolbar-items>
                <v-btn text @click="endDay">
                    Finalizar Dia
                </v-btn>
                <v-menu offset-y>
                    <template v-slot:activator="{ on, attrs }">
                        <v-btn v-bind="attrs" v-on="on" text>
                        Salvar & Carregar
                        </v-btn>
                    </template>
                    <v-list>
                        <v-list-item
                        v-for="(item, index) in items"
                        :key="index"
                        >
                        <v-list-item-title>{{ item.title }}</v-list-item-title>
                        </v-list-item>
                    </v-list>
                    </v-menu>
                    <div class="d-flex justify-center align-center">
                        <span>Saldo: {{funds | currency}}</span>
                    </div>
            </v-toolbar-items>
        </v-app-bar>
        <v-navigation-drawer app v-model="drawer">
            <v-list shaped>
                <v-list-item-group v-model="selectedItem" color="info">
                    <v-list-item v-for="(link, i) in links" :key="i" :to="link.route">
                        <v-list-item-title v-text="link.text"></v-list-item-title>
                        <v-list-item-icon>
                            <v-icon v-text="link.icon"></v-icon>
                        </v-list-item-icon>
                    </v-list-item>
                </v-list-item-group>
            </v-list>
        </v-navigation-drawer>
    </nav>
</template>


<script>
import {mapActions} from 'vuex'
export default {
    data: () => ({
        drawer: false,
        selectedItem: 0,
        links:[
            {icon: 'mdi-home-outline', text: 'Home Page', route: '/'},
            {icon: 'mdi-bank-transfer-out', text: 'Portfólio', route: '/portfolio'},
            {icon: 'mdi-bank-transfer-in', text: 'Ações', route: '/stocks'}
        ],
        items: [
        { title: 'Salvar Dados' },
        { title: 'Carregar Dados' },
      ]
    }),
    computed:{
        funds(){
            return this.$store.getters.funds
        }
    },
    methods:{
        ...mapActions(['randomizeStocks']),
        endDay(){
            this.randomizeStocks()
        }
    }
}
</script>


<style lang="scss" scoped>
nav{
    header{
        .v-toolbar__title{
            .vaiDaErrado{
                font-family: 'Courier New', Courier, monospace;
            }
            .vaiDaCerto{
                font-weight: 800;
            }
        }
    }
}
</style>