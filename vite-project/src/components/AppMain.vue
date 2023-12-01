<script>
import axios from "axios"
import searchText from "./SimpleTextToSearch.vue"
import BreweryCard from "./SimpleCard.vue"
import { store } from "../store.js"

export default {

    components: {
        BreweryCard,
        searchText
    },

    data() {
        return {
            store
        }
    },

    mounted() {
        this.getBrewery()
        console.log(this.store.breweries)
    },
    methods: {

        getBrewery() /* aggiorno per ricercare */ {
            let path = this.store.apiUrl;
            if (this.store.searchText.length !== 0) {
                path = `https://api.openbrewerydb.org/v1/breweries?by_postal=${parseInt(this.store.searchText)}`;
                console.log(path)
            }

            axios.get(path).then(result => {
                this.store.breweries = result.data;
            })
        }
    }
}

</script>

<template>
    <header>
        <searchText @search="getBrewery" />
    </header>
    <main>



        <BreweryCard v-for="card in store.breweries" :obj="card" />
        <p v-if="store.breweries.length == 0">Non ho Trovato Nulla
            inserisci un codice postale valido..</p>
    </main>
</template>

<style scoped></style>
