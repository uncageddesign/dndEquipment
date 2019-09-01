<template lang="html">
  <div class="details" v-if="item" id="equipmentDetail">
    <h3>{{item.name}}</h3>
    <p>Equipment Type: </p>
  </div>
</template>

<script>
import {eventBus} from '../main.js';

export default {
  name: 'equipment-details',
  props: ['equipment-details'],
  data(){
    return {
      item: null
    }
  },
  mounted(){
    // this.fetchItem();

    eventBus.$on('item-selected', (item) => {
      this.item = item
    })
  },
  updated() {
    // this.fetchItem();
  },
  methods: {
    // fetchItem() {
    //   fetch(this.equipment.url)
    //   .then(res => res.json())
    //   .then(details => details.url = detail.results)
    // }
  }
}

</script>

<style lang="css" scoped>
.details {
  border: solid 2px crimson;
  border-radius: 10px;
}

h3 {
  font-size: 30px;
}
</style>
