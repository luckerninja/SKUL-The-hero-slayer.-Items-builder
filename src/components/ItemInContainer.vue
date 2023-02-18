<template>
    <div class="item" :class="{itemWidth: isShowDescription}" draggable="true">
        <img @dragstart="startDrag($event, item.id)" @click="showDescription" :src="item.img" :class="{commonBorderRarity: item.rarity === 'Common' && borderRarity, rareBorderRarity: item.rarity === 'Rare' && borderRarity, uniqueBorderRarity: item.rarity === 'Unique' && borderRarity, legendaryBorderRarity: item.rarity === 'Legendary' && borderRarity}"/>
        <div class="itemDescription" :class="{showDescription: isShowDescription}">
            <span>{{ item.description }}</span>
            <ul>
                <template v-for="(effect, index) in item.effects" :key="index">
                    <li v-if="effect != ''">{{ effect }}</li>
                </template>
            </ul>
            <div class="inscriptions">
                <div>{{ item.inscription1 }}</div>
                <div>{{ item.inscription2 }}</div>
            </div>
        </div>
    </div>
</template>
<script>
    
    export default {
        data() {
            return {
                isShowDescription: false
            }
        },
        props: ['item', 'borderRarity'],
        methods: {
            showDescription() {
                if(this.isShowDescription) {
                    this.isShowDescription = false;
                } else {
                    this.isShowDescription = true;
                }
            },
            startDrag(event, itemId) {
                event.dataTransfer.dropEffect = 'move'
                event.dataTransfer.effectAllowed = 'move'
                event.dataTransfer.setData('itemId', itemId)
            }
        }
    }

    
</script>


<style>
    .item img {
        height: 80px;
        width: 80px;
        margin: 5px;
    }

    .commonBorderRarity {
        border: gray 3px solid;
    }

    .rareBorderRarity {
        border: orange 3px solid;
    }

    .uniqueBorderRarity {
        border: blue 3px solid;
    }

    .legendaryBorderRarity {
        border: yellow 3px solid;
    }

    .commonBorderRarity, .rareBorderRarity, .uniqueBorderRarity, .legendaryBorderRarity {
        height: 74px!important;
        width: 74px!important;
    }

    .itemDescription {
        display: none;
        background-color: black;
        color: white;
    }

    .showDescription {
        display: block;
        width: 100%;
        height: auto;
        padding: 20px;
    }

    .itemWidth {
        width: 100%;
    }


</style>