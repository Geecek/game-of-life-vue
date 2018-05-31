<template>
  <div class="cell" :class="{alive: alive}">
  </div>
</template>

<script>
export default {
  props: ['alive']
}
</script>

<style scoped>
  .cell {
    background-color: aliceblue;
    width: 14px;
    height: 14px;
    border-bottom: solid 1px;
    border-right: solid 1px;
    margin: 0px;
  }
  .alive {
    background-color: steelblue;
  }
</style>
