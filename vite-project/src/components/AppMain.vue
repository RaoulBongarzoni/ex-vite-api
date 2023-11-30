<script>
import axios from "axios"
import BreweryCard from "./SimpleCard.vue"
import { store } from "../store.js"

export default {

    components: {
        BreweryCard
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

        getBrewery() {
            axios.get(this.store.apiUrl).then(result => {
                this.store.breweries = result.data;
            });
        }
    }
}

</script>

<template>
    <main>
        <BreweryCard v-for="card in store.breweries" :obj="card" />
    </main>
</template>

<style scoped></style>
