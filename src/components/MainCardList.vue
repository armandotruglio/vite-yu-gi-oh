<script>
import CardListCard from './CardListCard.vue';

export default {
    data() {
        return {

        }
    },
    components: {
        CardListCard
    },
    props: {
        cardList: {
            type: Array,
            required: true,
        },
        loaded: {
            type: Boolean,
            required: true,
        }
    }
}


</script>

<template>
    <div class="card-list">

        <div class="loader" v-if="!this.loaded"></div>
        <div class="container" v-show="this.loaded">
            <div class="found-card-number">
                <h3 class="mb-4 text-center p-3 text-light">Carte trovate: {{ cardList.length }}</h3>
            </div>

            <div class="row">
                <div v-for="card in cardList" class="col-2">
                    <CardListCard :key="card.id" :cardName="card.name"
                        :cardImage="card.card_images[0].image_url_small" />
                </div>
            </div>
        </div>

    </div>
</template>

<style lang="scss" scoped>
.card-list {
    padding: 2rem;
    border: 20px solid brown;
    border-radius: 20px;

    h3 {
        background-color: brown;
        border-radius: 20px;
    }
}

/* HTML: <div class="loader"></div> */
.loader {
    width: fit-content;
    font-weight: bold;
    font-family: monospace;
    white-space: pre;
    font-size: 30px;
    line-height: 1.2em;
    height: 1.2em;
    overflow: hidden;

    position: absolute;
    right: 50%;
    top: 27%;
    transform: translate(50%, 27%);
}

.loader:before {
    content: "Loading...\A⌰oading...\A⌰⍜ading...\A⌰⍜⏃ding...\A⌰⍜⏃⎅ing...\A⌰⍜⏃⎅⟟ng...\A⌰⍜⏃⎅⟟⋏g...\A⌰⍜⏃⎅⟟⋏☌...\A⌰⍜⏃⎅⟟⋏☌⟒..\A⌰⍜⏃⎅⟟⋏☌⟒⏁.\A⌰⍜⏃⎅⟟⋏☌⟒⏁⋔";
    white-space: pre;
    display: inline-block;
    animation: l39 1s infinite steps(11) alternate;
}

@keyframes l39 {
    100% {
        transform: translateY(-100%)
    }
}
</style>