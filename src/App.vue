<template>
  <div id="app">
    <Calculator/>
  </div>
</template>

<script>
import Calculator from './components/Calculator'

export default {
  name: 'app',
  components: {
    Calculator
  }
}
</script>

<style>
  *{
    margin: 0;
    padding: 0;
  }
  #app{
    width: 100%;
    display: flex;
    justify-content: center;
    margin-top: 10%;
  }
</style>
