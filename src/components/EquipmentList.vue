<template lang="html">
  <div class="" id="equipmentList">
    <form v-on:submit.prevent>
      <input type="text" v-model="search" placeholder="search for item" v-on:keyup="searchForItem">
      <select v-on:change="handleSelect" v-model="selectedItem">
        <option disabled value="">Select Item</option>
        <option v-for="item in equipment" :value="item">{{item.name}}</option>
      </select>
    </form>
    <!-- <ul>
      <list-item v-for="(item, index) in equipment" :item="item" :key="index"></list-item>
    </ul> -->
  </div>
</template>

<script>
import {eventBus} from '../main.js'
// import ListItem from './ListItem.vue';

export default {
  name: 'equipment-list',
  data(){
    return {
      "search": "",
      "selectedItem": {}
    }
  },
  props: ['equipment'],
  methods: {
    searchForItem(){
      let foundItem = this.equipment.find((item) => {
        return item.name.toLowerCase().indexOf(this.search.toLowerCase()) > -1
      })
      this.selectedItem = foundItem

      eventBus.$emit('item-selected', this.selectedItem)
    },
    handleSelect(){
      this.search = ""
      eventBus.$emit('item-selected', this.selectedItem)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
