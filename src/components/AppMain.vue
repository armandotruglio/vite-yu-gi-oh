<script>
import MainCardList from "./MainCardList.vue"
import axios from 'axios';

export default {
    data() {
        return {
            apiArchetypeUrl: "https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0",
            apiCardUrl: "https://db.ygoprodeck.com/api/v7/cardinfo.php?num=60&offset=0",
            cardList: [],
            loaded: false,
        }
    },
    components: {
        MainCardList,
    },
    methods: {
        getCardsList() {
            axios.get(this.apiCardUrl).then((response) => {
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
    <main>
        <div class="container">
            <select name="Tipo" id="type">
                <option value="alien">Alien</option>
            </select>
        </div>
        <MainCardList :cardList="cardList" :loaded="loaded" />
    </main>
</template>

<style lang="scss" scoped>
main {
    background-color: orange;
    padding: 2rem;
    min-height: 100vh;

    select {
        width: 100px;
    }

}
</style>