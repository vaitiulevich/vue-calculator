<template>
  <div id="app">
  <Calculator/>
  </div>
</template>

<script>
import Calculator from './components/Calculator.vue'

export default {
  name: 'App',
  components: {
    Calculator
  }
}
</script>

<style>
body {
  background-color: rgb(32, 33, 39);
}
</style>
