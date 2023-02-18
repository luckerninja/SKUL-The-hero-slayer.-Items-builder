<template>
    <select name="inscriptionFilterSelector" class="inscriptionFilterSelector" @input="updateInscription">
        <option value="all">All</option>
        <option v-for="(option, index) in options" :value="option.name" :key="index">{{ option.name }}</option>
    </select>
    <label for="inscriptionFilterSelector">Inscription filter</label>
</template>
<script>
import inscriptions from '../assets/items/inscriptions.json'

export default {
    name: "inscriptionFilterSelector",
    data() {
        return {
            options: inscriptions.inscriptions
        }
    },
    props: ['selected'],
    emits: ['update:inscription'],
    methods: {
        updateInscription(event) {
            this.$emit('update:inscription', event.target.value);
        }
    }
}
</script>
<style>
    .inscriptionFilterSelector + label {
        color: white;
        padding-left: 5px;
    }
</style>