<template lang="html">
  <div class="details" v-if="equipmentDetails" id="equipmentDetail">
    <h3>{{item.name}}</h3>
    <hr>
      <p>Equipment Type: {{equipmentDetails.equipment_category}}</p>
      <p v-if="equipmentDetails.vehicle_category">Vehicle Category: {{equipmentDetails.vehicle_category}}</p>
      <p v-if="equipmentDetails['weapon_category:']">Category: {{equipmentDetails['weapon_category:']}}</p>
      <p v-if="equipmentDetails.weapon_range">Weapon Range: {{equipmentDetails.weapon_range}}</p>
      <p v-if="equipmentDetails.damage">Damage Type: {{equipmentDetails.damage.damage_type.name}}
    </br>Dice: {{equipmentDetails.damage.dice_count}} x D{{equipmentDetails.damage.dice_value}}
      </p>
      <p v-if="equipmentDetails.weight">Weight: {{equipmentDetails.weight}}</p>
      <p v-if="equipmentDetails.speed">Speed: {{equipmentDetails.speed.quantity}} {{equipmentDetails.speed.unit}}</p>
      <p v-if="equipmentDetails.capacity">Capacity: {{equipmentDetails.capacity}}</p>
      <!-- <p v-if="equipmentDetails.properites">Properties: <ul v-for="property in properties">
                                                          <li>{{equipmentDetails.properties.name}}</li>
                                                        </ul>
      </p> -->
      <p>Cost: {{equipmentDetails.cost.quantity}} {{equipmentDetails.cost.unit}}</p>
      <p v-if="equipmentDetails.desc">Description: {{equipmentDetails.desc[0]}}</p>
  </div>
</template>

<script>
import {eventBus} from '../main.js';

export default {
  name: 'equipment-details',
  // props: ['equipment-details'],
  data() {
    return {
      item: null,
      equipmentDetails: null
    }
  },
  mounted(){

    eventBus.$on('item-selected', (item) => {
      this.item = item;
      this.fetchItem();
    })
  },
  updated() {
    // this.fetchItem();
  },
  methods: {
    fetchItem() {
      fetch(this.item.url)
      .then(res => res.json())
      .then(data => {
        this.equipmentDetails = data;
      })
    }
  }
}

</script>

<style lang="css" scoped>
.details {
  border: solid 2px crimson;
  border-radius: 5px;
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
