<template>
  <div id="app">
  <h1> Vue Calculator </h1>
  <calculator></calculator>
    
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

</style>
