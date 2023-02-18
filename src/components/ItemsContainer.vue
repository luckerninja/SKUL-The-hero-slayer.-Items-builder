<template>
    <div class="itemsContainer">
        <ItemInContainer v-for="(item, index) in filteredItems" :key="index" :id="index" :item="item" :borderRarity="borderRarity"/>
    </div>
</template>
<script>
import items from '../assets/items/items.json'
import ItemInContainer from './ItemInContainer.vue';

console.log(items.items)

export default {
    data() {
        return {
            items: items.items
        }
    },
    props: ['borderRarity', 'rarityFilter', 'inscriptionFilter'],
    components: {
        ItemInContainer
    },
    computed: {
        filteredItems() {
            // return this.items
            return this.items.filter(item => {
                const rarityCondition = this.rarityFilter == 'all' ? true : item.rarity == this.rarityFilter;
                const inscriptionCondition1 = this.inscriptionFilter == 'all' ? true : item.inscription1 == this.inscriptionFilter;
                const inscriptionCondition2 = this.inscriptionFilter == 'all' ? true : item.inscription2 == this.inscriptionFilter;

                // console.log(rarityCondition,  inscriptionCondition1, inscriptionCondition2)

                return (rarityCondition && (inscriptionCondition1 || inscriptionCondition2));
            });
        }
    }
}

//['name', 'rarity', 'description', 'inscription1', 'inscription1', 'effects', 'img']
</script>
<style>
    .itemsContainer {
        width: 40%;
        margin: 0 auto;
        display: flex;
        justify-content: left;
        flex-wrap: wrap;
    }
</style>