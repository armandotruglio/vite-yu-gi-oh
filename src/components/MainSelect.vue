<script>
export default {
    data() {
        return {
            selectedArchetype: "",
        }
    },
    props: {
        cardArchetypeList: {
            type: Array,
            required: true,
        }
    },
    methods: {
        archetypeSelected(archetype) {
            this.$emit("archetypeSelected", archetype);
        }
    }
}
</script>

<template>
    <div class="container mb-5">
        <select v-model="selectedArchetype" @change="archetypeSelected(selectedArchetype)">
            <option disabled value="">Scegli un archetipo</option>
            <option v-for="(archetype, index) in cardArchetypeList" :key="index" :value="archetype.archetype_name">
                {{ archetype.archetype_name }}
            </option>
        </select>
    </div>
</template>

<style scoped></style>