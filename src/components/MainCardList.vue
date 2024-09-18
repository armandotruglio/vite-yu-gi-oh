<script>
import axios from 'axios';
import CardListCard from './CardListCard.vue';

export default {
    data() {
        return {
            apiUrl: "https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0",
            cardList: [],
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

        }
    },
    created() {
        this.getCardsList();
    }
}


</script>

<template>
    <div class="card-list">
        <div class="container">
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
</style>