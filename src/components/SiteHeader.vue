<template lang="html">
  <div id="header">
    <h1>Equip Thy Party</h1>
  </div>
</template>

<script>
export default {
  name: 'site-header',
}
</script>

<style lang="css" scoped>
  #header {
    max-height: 350px;
    padding: 50px;
    background-color: whitesmoke;
    background-image: url('../assets/bookart.jpeg');
    border-bottom: solid 10px crimson;
  }

  h1 {
    font-family: sans-serif;
    font-size: 70px;
    color: whitesmoke;
    background-color: rgba(0, 0, 0, 0.5);
    padding: 5px;
    width: 500px
  }
</style>
