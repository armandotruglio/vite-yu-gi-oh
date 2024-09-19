<script>
import MainCardList from "./MainCardList.vue"
import MainSelect from "./MainSelect.vue";
import axios from 'axios';

export default {
    data() {
        return {
            apiArchetypeUrl: "https://db.ygoprodeck.com/api/v7/archetypes.php",
            apiCardUrl: "https://db.ygoprodeck.com/api/v7/cardinfo.php?num=60&offset=0",
            cardList: [],
            cardArchetypeList: [],
            loaded: false,
        }
    },
    components: {
        MainCardList,
        MainSelect,
    },
    methods: {
        //Funzione che chiama API che fornisce la lista di archetipi di carte
        getCardArchetype() {
            axios.get(this.apiArchetypeUrl).then((response) => {
                this.cardArchetypeList = response.data;
            })
        },
        //Funzione che chiama API che fornisce una lista di massimo 60 carte eventualmente filtrate per archetipo
        getCardsList(archetype = "") {
            if (archetype === "") {
                axios.get(this.apiCardUrl).then((response) => {
                    this.cardList = response.data.data;
                })
            }
            else {
                axios.get(this.apiCardUrl, {
                    params: {
                        archetype: archetype
                    }
                }).then((response) => {
                    this.cardList = response.data.data;
                })
            }

            setTimeout(() => {
                this.loaded = true;
            }, 500);
        },
        getFilteredCardList(archetype) {
            this.loaded = false;
            this.getCardsList(archetype);
        }
    },
    created() {
        //Chiamata iniziale alle funzioni che chiamano le API
        this.getCardArchetype();
        this.getCardsList();
    }
}
</script>

<template>
    <main>
        <MainSelect :cardArchetypeList="cardArchetypeList" @archetypeSelected="getFilteredCardList" />
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