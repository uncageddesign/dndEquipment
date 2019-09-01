<template lang="html">
  <div class="">

  </div>
</template>

<script>
import {eventBus} from '../main.js';

export default {
  name: 'equipment-dropdown',
  props: ['equipment'],
  data(){
    return {
      dropdownEquipment: null,
      searchText: ""
    }
  },
  methods: {
    handleChange() {
      this.search = "";
      eventBus.$emit('equipment-selected',
      this.dropdownEquipment)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
