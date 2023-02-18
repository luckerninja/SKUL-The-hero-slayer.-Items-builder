<template>
    <div class="inventorySlot" @drop="onDrop($event, 1)" @dragover.prevent @dragenter.prevent>
        <img v-if="itemId != -1" :src="itemId != -1 ? items[itemId].img : ''">
    </div>
</template>
<script>
import items from '../assets/items/items.json'

export default {
    data() {
        return {
            itemId: -1,
            items: items.items
        }
    },
    props: ['slotId'],
    methods: {
        onDrop(event) {
            const itemId = event.dataTransfer.getData('itemId')
            if(itemId) {
                this.itemId = itemId;
                this.$emit('slot-change', {
                    id: this.slotId,
                    inscriptions: [
                        this.items[itemId].inscription1,
                        this.items[itemId].inscription2
                    ]
                })
            }
        }
    }
}
</script>
<style>
    .inventorySlot {
        height: calc(30% - 16px);
        width: calc(30% - 16px);
        margin: 10px;
        background-color: #B2977B;
        border: #050E1C 3px solid;
        border-radius: 10px;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .inventorySlot img {
        width: 90%;
        height: 90%;
    }
</style>