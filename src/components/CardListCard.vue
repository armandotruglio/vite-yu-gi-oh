<script>
export default {
    data() {
        return {

        }
    },
    props: {
        cardImage: {
            type: String,
            required: true,
        },
        cardName: {
            type: String,
            required: true,
        }
    }
}
</script>

<template>
    <div class="single-card">
        <figure>
            <img class="img-fluid" :src=cardImage alt="cardName">
        </figure>
        <h4 class="text-light">{{ cardName }}</h4>
    </div>
</template>

<style scoped></style>