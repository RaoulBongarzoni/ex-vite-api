<script>
export default {
    name: "SimpleCard",
    props: {
        obj: "object"

    }
}
</script>

<template>
    <div class="card-wrapper">
        <div class="card">
            <h2>{{ obj.name }}</h2>
            <span>
                <p>{{ obj.street }}</p>

                <p>{{ obj.city }}</p>
            </span>
            <a :href="obj.website_url">Sito web</a>
        </div>
    </div>
</template>


<style></style>