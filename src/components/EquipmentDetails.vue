<template lang="html">
  <div class="" v-if="item" id="equipmentDetail">
    <h2>{{item.name}}</h2>
    <p>Equipment Type: </p>
  </div>
</template>

<script>
import {eventBus} from '../main.js';

export default {
  name: 'equipment-details',
  data(){
    return {
      item: null
    }
  },
  mounted(){
    eventBus.$on('item-selected', (item) => {
      this.item = item
    })
  }
}
</script>

<style lang="css" scoped>
</style>
