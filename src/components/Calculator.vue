<template>
  <div id="calculator">
    <div class="display">{{display}}</div>
    <button class="h-operator" @click="clear">C</button>
    <button class="h-operator" @click="negate">+/-</button>
    <button class="h-operator" @click="setOperation('percentage')">%</button>
    <button class="operator" @click="setOperation('divide')">/</button>
    <button class="numerical" @click="displayNumerical('7')">7</button>
    <button class="numerical" @click="displayNumerical('8')">8</button>
    <button class="numerical" @click="displayNumerical('9')">9</button>
    <button class="operator" @click="setOperation('multiply')">X</button>
    <button class="numerical" @click="displayNumerical('4')">4</button>
    <button class="numerical" @click="displayNumerical('5')">5</button>
    <button class="numerical" @click="displayNumerical('6')">6</button>
    <button class="operator" @click="setOperation('subtract')">-</button>
    <button class="numerical" @click="displayNumerical('1')">1</button>
    <button class="numerical" @click="displayNumerical('2')">2</button>
    <button class="numerical" @click="displayNumerical('3')">3</button>
    <button class="operator" @click="() => setOperation('add')">+</button>
    <button class="zero" @click="displayNumerical('0')">0</button>
    <button class="numerical" @click="() => {if(singleDecimalAllowed) displayNumerical('.')}">.</button>
    <button class="operator" @click="result">=</button>
  </div>
</template>

<script>
  export default {
    name: "Calculator",
    data() {
      return {
        a: '',
        b: '',
        display: '0',
        operation: '',
        singleDecimalAllowed: true
      }
    },
    methods: {
      displayNumerical: function (num) {
        if (!this.operation) {
          this.a += num;
          if (num === '.')
            this.singleDecimalAllowed = false;
          if (this.a[0] === '0')
            this.a = '';
          if (this.a) this.display = this.a;
        }
        else {
          this.b += num;
          if (num === '.')
            this.singleDecimalAllowed = false;
          if (this.b[0] === '0')
            this.b = '';
          if (this.b) this.display = this.b;
        }
      },
      setOperation: function (operator) {
        this.operation = operator;
        this.singleDecimalAllowed = true;
        this.result();
      },
      negate: function () {
        if (!this.operation) {
          if (this.display !== '0') {
            this.a = '-' + this.a;
            this.display = this.a;
          }
          else
            this.display = '0';
        } else {
          if (this.display !== '0')
            this.b = '-' + this.b;
          this.display = this.b;
        }
      },
      result: function () {
        if (this.a && this.b) {
          if(this.operation === 'add')
            this.display = parseFloat(this.a) + parseFloat(this.b);
          else if(this.operation === 'subtract')
            this.display = parseFloat(this.a) - parseFloat(this.b);
          else if(this.operation === 'multiply')
            this.display = parseFloat(this.a) * parseFloat(this.b);
          else if(this.operation === 'divide')
            this.display = parseFloat(this.a) / parseFloat(this.b);
          else if(this.operation === 'percentage')
            this.display = (parseFloat(this.a) * parseFloat(this.b))/100;
          this.a = this.display;
          this.b = '';
        }else{
          this.a = this.display;
          this.b = '';
        }
      },
      clear: function () {
        this.a = '';
        this.b = '';
        this.display = '0';
        this.operation = '';
        this.singleDecimalAllowed = true;
      }
    }
  }
</script>

<style scoped>

  #calculator {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    border-right: 1px solid black;
    border-bottom: 1px solid black;
  }

  .display {
    grid-column: 1/end;
    color: #fff;
    background: black;
  }

  .zero {
    grid-column: 1/3;
  }

  button {
    outline: none;
    border: none;
    background: white;
    /*text-decoration: none;*/
  }

  button:hover {
    -webkit-transition-duration: 0.4s; /* Safari */
    transition-duration: 0.4s;
    box-shadow: 0 12px 16px 0 rgba(0, 0, 0, 0.24), 0 17px 50px 0 rgba(0, 0, 0, 0.19);
  }

  button:active {
    opacity: 0.8;
    box-shadow: 0 5px #666;
  }

  .display, .operator, .h-operator, .zero, .numerical {
    min-width: 64px;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 48px;
    padding: 0 8px;
    border-top: 1px solid black;
    border-left: 1px solid black;
  }

  .zero, .numerical {
    color: rgba(0, 0, 0, 0.8);
  }

  .operator, .h-operator {
    background: coral;
    color: bisque;
  }
</style>