<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div class="row justify-content-center py-3">
      <div class="col-md-6">
        <table class="table table-bordered">
          <tbody>
            <tr class="output">
              <td colspan="4">
              {{ output || 0 }}
              </td>
            </tr>
            <tr>
              <td v-on:click="clearField">C</td>
              <td v-on:click="setNegativeOrPositive">+/-</td>
              <td v-on:click="calculatePercentage">%</td>
              <td class="lastcolumn"><i class="fa-solid fa-divide"></i></td>
            </tr>
            <tr>
              <td>7</td>
              <td>8</td>
              <td>9</td>
              <td class="lastcolumn"><i class="fa-solid fa-xmark"></i></td>
            </tr>
            <tr>
              <td>4</td>
              <td>5</td>
              <td>6</td>
              <td class="lastcolumn">-</td>
            </tr>
            <tr>
              <td>1</td>
              <td>2</td>
              <td>3</td>
              <td class="lastcolumn">+</td>
            </tr>
            <tr>
              <td colspan="2">0</td>
              <td>.</td>
              <td class="lastcolumn">=</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Calculator",
  props: {
    msg: String,
  },
  data() {
    return {
      output: '100'
    }
  },
  methods: {
   clearField() {
     this.output = '';
   },
   setNegativeOrPositive() {
     this.output = this.output[0] === '-' ? this.output.slice(1) : `-${this.output}`;
   },
   calculatePercentage() {
     this.output = parseFloat(this.output)/100;
   }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.output {
  background-color: #333;
  color: #fff;
}
.lastcolumn {
  background-color: orange; 
  color: #fff;
}
.lastcolumn:active {
  background-color: #333;
  color: #fff;
}
</style>
