<script>
import MainCardList from "./MainCardList.vue"
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
    },
    methods: {
        getCardArchetype() {
            axios.get(this.apiArchetypeUrl).then((response) => {
                console.log(response.data);
                this.cardArchetypeList = response.data;
            })
        },
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
        this.getCardArchetype();
        this.getCardsList();
    }
}
</script>

<template>
    <main>
        <div class="container">
            <select name="Tipo" id="type">
                <option v-for="(archetype, index) in cardArchetypeList" :key="index" value="archetype.archetype_name">
                    {{ archetype.archetype_name }}
                </option>
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