<template>
  <div id="app">
    <site-header></site-header>
    <equipment-list :equipment="equipment"></equipment-list>
    <div class="details">
      <h2>Find Your Loot</h2>
      <equipment-details :item="selectedEquipment"></equipment-details>
    </div>
  </div>
</template>

<script>
import EquipmentList from './components/EquipmentList.vue';
import EquipmentDetails from './components/EquipmentDetails.vue';
import SiteHeader from './components/SiteHeader.vue';
import {eventBus} from './main.js';

export default {
  name: 'app',
  data(){
    return {
      equipment: [],
      selectedEquipment: null
    }
  },
  mounted(){
    fetch('http://www.dnd5eapi.co/api/equipment/')
    .then(res => res.json())
    .then(equipment => this.equipment = equipment.results)

    eventBus.$on('equipment-selected', (item) => {
      this.selectedEquipment = item;
    })
  },
  components: {
    'equipment-list': EquipmentList,
    'equipment-details': EquipmentDetails,
    'site-header': SiteHeader
  }
}
</script>

<style>
.details {
  min-height: 50px;
  background-color: whitesmoke;
  padding: 10px;
  font-family: sans-serif;
}

h2 {
  font-size: 40px;
}
</style>
