<template>
  <section>
    <div class="header">
      <h1>The game of life</h1>
    </div>
    <Board />
    <Settings />
  </section>
</template>

<script>
import Board from './components/Board'
import Settings from './components/Settings'

export default {
  name: 'app',
  components: {Board, Settings}
}
</script>

<style>
</style>
