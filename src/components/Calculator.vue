<template>
  <div id="calculator">
    <div class="display">45</div>
    <button class="h-operator">C</button>
    <button class="h-operator">+/-</button>
    <button class="h-operator">%</button>
    <button class="operator">/</button>
    <button class="numerical">7</button>
    <button class="numerical">8</button>
    <button class="numerical">9</button>
    <button class="operator">X</button>
    <button class="numerical">4</button>
    <button class="numerical">5</button>
    <button class="numerical">6</button>
    <button class="operator">-</button>
    <button class="numerical">1</button>
    <button class="numerical">2</button>
    <button class="numerical">3</button>
    <button class="operator">+</button>
    <button class="zero">0</button>
    <button class="numerical">.</button>
    <button class="operator">=</button>
  </div>
</template>

<script>
  export default {
    name: "Calculator"
  }
</script>

<style scoped>
  button{
    outline: none;
    border: none;
    background: white;
    /*text-decoration: none;*/
  }
  button:hover{
    -webkit-transition-duration: 0.4s; /* Safari */
    transition-duration: 0.4s;
    box-shadow: 0 12px 16px 0 rgba(0,0,0,0.24), 0 17px 50px 0 rgba(0,0,0,0.19);
  }
  button:active {
    opacity: 0.8;
    box-shadow: 0 5px #666;
  }
  #calculator{
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    border-right: 1px solid black;
    border-bottom: 1px solid black;
  }
  .display{
    grid-column: 1/end;
    color: #fff;
    background: black;
  }
  .zero{
    grid-column: 1/3;
  }
  .display, .operator,.h-operator, .zero, .numerical{
    min-width: 64px;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 48px;
    padding: 0 8px;
    border-top: 1px solid black;
    border-left: 1px solid black;
  }
  .zero, .numerical{
    color: rgba(0,0,0,0.8);
  }
  .operator, .h-operator{
    background: coral;
    color: bisque;
  }
</style>