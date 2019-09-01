<template lang="html">
  <li v-on:click="handleClick">{{item.name}}</li>
</template>

<script>
import {eventBus} from '../main.js';

export default {
  name: "list-item",
  props: ['item'],
  methods: {
    handleClick(){
      eventBus.$emit('equipment-selected',
      this.item);
    }
  }
}
</script>

<style lang="css" scoped>
</style>
