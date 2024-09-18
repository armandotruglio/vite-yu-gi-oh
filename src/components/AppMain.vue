<script>
import MainCardList from "./MainCardList.vue"
export default {
    data() {
        return {

        }
    },
    components: {
        MainCardList,
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
        <MainCardList />
    </main>
</template>

<style lang="scss" scoped>
main {
    background-color: orange;
    padding: 2rem;

    select {
        width: 100px;
    }

}
</style>