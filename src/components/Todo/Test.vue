<template>
  <div class="hello">
    <h3>Vuejs Input type number validation</h3>
    <br />

    <input type="text" placeholder="Enter Number" v-model="inputValue"  @input="change($event)"
      @change="change($event)"/>
    <div class="error" v-if="!isValid">Number is Invalid</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      mynumber: "",
      isValid: true,
      regex: /[0-9]/,
      max: 3
    };
  },
  computed:{
    getMynumber() {
        return this.mynumber
    },
    inputValue: {
        get () {
            return this.mynumber >= this.max ?  this.max : this.mynumber
        },
        set (value) {
            value = value >= this.max ?  this.max : value
            console.log(value)
            const targetValue = parseInt(value, 10)
            if (!isNaN(targetValue)) {
                this.$emit('input', targetValue !== 0 ? Math.abs(targetValue) : 0)
            }
        }
    }
  },
  methods: {
    change:function(e){
        console.log(e.target.value)
      const number = e.target.value
      this.isNumberValid(number);
    },
    isNumberValid: function(inputNumber) {
      this.isValid=   this.regex.test(inputNumber)
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.error{
  color:red;
}
</style>