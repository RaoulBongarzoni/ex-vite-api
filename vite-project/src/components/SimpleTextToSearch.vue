<script>
import { store } from "../store.js"

export default {
    name: "SearchBar",

    data() {
        return {
            store
        }
    },
    methods: {
        search() {
            this.$emit("search")
        }


    }




}
</script>

<template>
    <div>
        <input v-model="store.searchText" @keyup.enter="$emit('search')">
        <button @click="search">cerca</button>

    </div>
</template>

<style></style>