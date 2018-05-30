<template>
  <section>
    <div class="header">
      <h1>The game of life</h1>
    </div>
    <Board />
  </section>
</template>

<script>
import Board from './components/Board'

export default {
  name: 'app',
  components: {Board}
}
</script>

<style>
</style>
