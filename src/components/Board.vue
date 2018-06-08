<template>
  <div class="board">
    <Cell @changeState="changeState" v-for="(cell, index) in state.grid" :alive="cell" :key="index" :index="index"/>
  </div>
</template>

<script>
import Cell from './Cell'
export default {
  data () {
    return {
      state: {
        height: 50,
        width: 80,
        grid: []
      },
      loop: null,
      interval: 50
    }
  },
  computed: {
    moves () {
      return [
        this.state.width + 1,
        this.state.width,
        this.state.width - 1,
        1,
        -1,
        -this.state.width + 1,
        -this.state.width,
        -this.state.width - 1
      ]
    }
  },
  components: {Cell},
  created () {
    this.initGrid()
    this.enterLoop()
  },
  methods: {
    initGrid () {
      this.state.grid = Array.from({length: this.state.height * this.state.width}, () => {
        return Math.random() < 0.2
      })
    },
    numberOfNeighbours (index) {
      return this.moves
        .map(move => {
          if (index - move < 0 || index - move > this.state.height * this.state.width) { // this is bad but stays for now
            return 0
          }
          return this.state.grid[index - move] ? 1 : 0
        })
        .reduce((acc, curr) => {
          return acc + curr
        })
    },
    enterLoop () {
      this.loop = setInterval(() => {
        this.state.grid = this.state.grid.map((cell, index) => {
          const neighbours = this.numberOfNeighbours(index)
          if (neighbours < 2 || neighbours > 3) {
            return false
          }
          if (neighbours === 3) {
            return true
          }
          return cell
        })
      }, this.interval)
    },
    changeState (index) {
      this.state.grid[index] = !this.state.grid[index]
    }
  }
}
</script>

<style scoped>
  .board {
    width: 450px;
    display: grid;
    grid-template-columns: repeat(80, 1fr);
  }
</style>
