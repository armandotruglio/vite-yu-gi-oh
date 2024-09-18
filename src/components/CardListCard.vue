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
    <img :src=cardImage alt="OK">
    <span>{{ cardName }}</span>
</template>

<style scoped></style>