<template lang="html">
  <div class="details" v-if="item" id="equipmentDetail">
    <h3>{{item.name}}</h3>
    <hr>
      <p>Equipment Type: </p>
      <p>Category: </p>
      <p>Range: </p>
      <p>Damaged:
      </br>Type:
      </p>
      <p>Weight: </p>
      <p>Speed: </p>
      <p>Properties: </p>
      <p>Cost: </p>
      <p>Description: </p>
  </div>
</template>

<script>
import {eventBus} from '../main.js';

export default {
  name: 'equipment-details',
  // props: ['equipment-details'],
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
  padding: 20px;
  max-width: 800px;
  margin-left: 40px;
  margin-top: 20px;
}

h3 {
  font-size: 30px;
}

p {
  padding: 5px;
}

hr {
  margin: 10px 0 10px 0;
}

</style>
