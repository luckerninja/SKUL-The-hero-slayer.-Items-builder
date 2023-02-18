<template>
    <!-- <input class="rarityBorderCheckbox" type="checkbox" :checked="checked" @change="updateCheckbox"  /> -->
    <select name="rarityFilterSelector" class="rarityFilterSelector" @input="updateRarity">
        <option value="all">All</option>
        <option value="Common">Common</option>
        <option value="Rare">Rare</option>
        <option value="Unique">Unique</option>
        <option value="Legendary">Legendary</option>
    </select>
    <label for="rarityFilterSelector">Rarity filter</label>
</template>
<script>

export default {
    name: "rarityFilterSelector",
    props: ['selected'],
    emits: ['update:rarity'],
    methods: {
        updateRarity(event) {
            this.$emit('update:rarity', event.target.value)
        }
    }
}
</script>
<style>
    .rarityFilterSelector + label {
        color: white;
        padding-left: 5px;
    }
</style>