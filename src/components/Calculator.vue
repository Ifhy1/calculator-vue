<template>
  <div class="p-3" style="max-width: 400px; margin: 40px auto; background: #234">

  <!--calculator result-->
  <div class="w-full rounded m-1 p-3 text-right lead font-weight-bold text-white bg-vue-dark">
  
  {{ calculatorValue || 0 }}
  </div>

  <!--Calculator buttons-->
  <div class="row no-gutters">
    <div class="col-3" v-for="n in calculatorElements" :key="n">
    <div class="lead text-white text-center m-1 py-3 bg-vue-dark rounded hover-class"
      :class="{'bg-vue-black' : ['c','*','/','-','+','%','='].includes(n)}"
      @click="action(n)"
    
    >
    {{n}}
    
    </div>

  </div>
</template>

<script>
export default {
  name: 'Calculator',
  props: {
    msg: String
  },

  data() {
    return {
      calculatorValue: '',
      calculatorElements: ['c','*','/','-','7','8','9','+','4','5','6','%','1','2','3','=','0','.'],
      operator: null,
      previousCalculatorValue: '',
      
     

    }
  },


  methods: {
    action(n) {
      if(!isNaN(n)  || n === '.') {
        this.calculatorValue += n + '';
      }
     
     if(n === 'c') {
       this.calculatorValue = '';
     }

     if(n === '%') {
       this.calculatorValue = this.calculatorValue / 100 + '';
     }

     if(['/','*','-','+'].includes(n)){
       this.operator = n;
       this.previousCalculatorValue = this.calculatorValue;
       this.calculatorValue = '';
     }

     if(n === '='){
       this.calculatorValue = eval(
         this.previousCalculatorValue + this.operator + this.calculatorValue
       );
      this.previousCalculatorValue = '',
      this.operator = null;
     }
    }
  }

}


</script>

<style scoped>
.bg-vue-dark {
  background: orange;
}
.hover-class: hover {
  cursor: pointer;
  background: white;
}
.bg-vue-black {
  background: black;
}

</style>