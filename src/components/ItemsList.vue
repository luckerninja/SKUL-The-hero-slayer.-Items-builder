<template>
    <div class="items">
        <div class="itemsMenu">
            <RarityBorderCheckbox v-model:checked="stylizationConfig.rarityBorder"/>
            <RarityFilterSelector v-model:rarity="stylizationConfig.rarity"/>
            <InscriptionFilterSelector v-model:inscription="stylizationConfig.inscription"/>
        </div>
        <ItemsContainer :borderRarity="stylizationConfig.rarityBorder" :rarityFilter="stylizationConfig.rarity" :inscriptionFilter="stylizationConfig.inscription"/>
    </div>
</template>
<script>
import ItemsContainer from './ItemsContainer.vue';
import RarityBorderCheckbox from './RarityBorderCheckbox.vue';
import RarityFilterSelector from './RarityFilterSelector.vue';
import InscriptionFilterSelector from './InscriptionFilterSelector.vue';

export default {
    data() {
        return {
            stylizationConfig: {
                rarityBorder: false,
                rarity: 'all',
                inscription: 'all'
            }

        }
    },
    components: {
        ItemsContainer,
        RarityBorderCheckbox,
        RarityFilterSelector,
        InscriptionFilterSelector
    }
    
}
</script>
<style>
    .itemsMenu {
        width: 40%;
        margin: 0 auto;
    }

    .itemsMenu select {
        margin-left: 10%;
    }
</style>