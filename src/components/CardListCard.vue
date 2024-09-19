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
            <img class="img-fluid card-front" :src=cardImage alt="cardName">
        </figure>
        <h4 class="fs-5 text-light text-center">{{ cardName }}</h4>
    </div>
</template>

<style lang="scss" scoped></style>