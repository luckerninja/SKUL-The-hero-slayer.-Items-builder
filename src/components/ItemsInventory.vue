<template>
    <div class="itemsInventory">
        <InventorySlot @slot-change="changeSlot" v-for="(slot, index) in 9" :key="slot" :slotId="index"/>
    </div>
</template>
<script>
import InventorySlot from './InventorySlot.vue';

export default {
  data() {
    return {
      slots: {}
    }
  },
  components: {
    InventorySlot
  },
  methods: {
    changeSlot(event) {
      this.slots[event.id] = event.inscriptions
      this.$emit('slots-change', {
        slots: this.slots
      })
    }
  }
}
</script>
<style>
    .itemsInventory {
        background-color: #D9C3B3;
        width: 300px;
        height: 300px;
        margin: 20px auto;
        display: flex;
        flex-wrap: wrap;
        justify-content: space-around;
        align-items: center;
        border-radius: 10px;
    }
</style>