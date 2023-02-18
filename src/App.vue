<template>
  <SiteDescription />
  <InscriptionsMenu :slots="slots"/>
  <ItemsInventory @slots-change="inscriptionsUpdate"/>
  <ItemsList />
</template>

<script>
import ItemsInventory from './components/ItemsInventory.vue';
import ItemsList from './components/ItemsList.vue';
import SiteDescription from './components/SiteDescription.vue';
import InscriptionsMenu from './components/InscriptionsMenu.vue';

export default {
  name: 'App',
  data() {
    return {
      slots: {}
    }
  },
  components: {
    ItemsInventory,
    ItemsList,
    SiteDescription,
    InscriptionsMenu
  }, 
  methods: {
    inscriptionsUpdate(event) {
      console.log(event, 'aa')
      this.slots = event.slots
    }
  }
}
</script>

<style>

  @import url('https://fonts.googleapis.com/css2?family=VT323&display=swap');

  * {
    margin: 0;
    padding: 0;
    font-family: 'VT323', monospace;
  }

  a {
    color: #be3cfd;
  }

  body {
    background-color: #1f0c33;
  }

</style>
