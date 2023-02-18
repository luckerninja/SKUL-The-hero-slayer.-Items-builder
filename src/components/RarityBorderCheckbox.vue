<template>
        <input class="rarityBorderCheckbox" type="checkbox" :checked="checked" @change="updateCheckbox" name="rarityBorderCheckbox" />
        <label for="rarityBorderCheckbox">Show rarity borders</label>
</template>
<script>
export default {
        name: "rarityBorderCheckbox",
        props: ['checked'],
        emits: ['update:checked'],
        methods: {
            updateCheckbox(event) {
                this.$emit('update:checked', event.target.checked)
            }
        }
}
</script>
<style>
    .rarityBorderCheckbox + label {
        color: white;
        padding-left: 5px;
    }
</style>