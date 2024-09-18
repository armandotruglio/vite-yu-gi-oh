<script>
import axios from 'axios';
import CardListCard from './CardListCard.vue';

export default {
    data() {
        return {
            apiUrl: "https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0",
            cardList: [],
            loaded: false,
        }
    },
    components: {
        CardListCard
    },
    methods: {
        getCardsList() {
            axios.get(this.apiUrl).then((response) => {
                console.log(response.data.data);
                this.cardList = response.data.data;
            })

            setTimeout(() => {
                this.loaded = true;
            }, 2000);
        }
    },
    created() {
        this.getCardsList();
    }
}


</script>

<template>
    <div class="card-list">
        <div class="loader" v-if="!this.loaded"></div>
        <div class="container" v-show="this.loaded">
            <div class="row">
                <div v-for="card in cardList" class="col-3">
                    <CardListCard :key="card.id" :cardName="card.name"
                        :cardImage="card.card_images[0].image_url_small" />
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.card-list {
    padding: 2rem;
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
    top: 50%;
    transform: translate(50%, 50%);
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