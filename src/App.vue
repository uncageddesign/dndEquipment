<template>
  <div id="app">
    <site-header></site-header>
    <equipment-list :equipment="equipment"></equipment-list>
    <equipment-details :item="selectedEquipment"></equipment-details>
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
#app {

}
</style>
