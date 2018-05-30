<template>
  <div class="board">
    <Cell v-for="(cell, index) in state.grid" :state="cell" :key="index"/>
  </div>
</template>

<script>
import Cell from './Cell'
export default {
  data () {
    return {
      state: {
        height: 20,
        width: 30,
        grid: []
      }
    }
  },
  components: {Cell},
  created () {
    this.initGrid()
    console.log(this.state.grid)
  },
  methods: {
    initGrid () {
      this.state.grid = Array.from({length: this.state.height * this.state.width}, () => {
        return {
          alive: Math.random() < 0.1
        }
      })
    }
  }
}
</script>

<style scoped>
  .board {
    width: 450px;
    display: grid;
    grid-template-columns: repeat(30, 1fr);
  }
</style>
