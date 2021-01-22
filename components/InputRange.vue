<template>
  <div class="hello">
    <div class="range-slider">
    <span class="left" @click="minus()">-</span>
    <input type="range" :value="value" @input="onInput" :min="min" :max="max" :step="step">
    <span class="right" @click="plus()">+</span>
  </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
   props: {
    value: {
      type: Number,
      default: 0,
    },
    min: {
      type: Number,
      default: 0
    },
    max: {
      type: Number,
      default: 100
    },
    step: {
      type: Number,
      default: 1
    }
  },
  data: function () {
    return {
      // mutate value to range for recomendation vue core
      range: this.value
    }
  },
  methods: {
    onInput (e) {
      this.$emit('input', e.target.value)
    },
    plus: function () {
      if (this.range < this.max) {
         this.range = parseInt(this.range) + parseInt(this.step);
        if (this.range > this.max) {
           this.range = this.max;
        }
      }
    },
    minus: function () {
      if (this.range > this.min) {
         this.range = parseInt(this.range) - parseInt(this.step);
         if (this.range < this.min) {
           this.range = this.min;
         }
      }
    }
  },
  watch: {
    range: function () {
      this.$emit('input', this.range)
    },
    value: function () {
      this.range = this.value
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">$brand-primary: #3f51b5;
$body-bg: #111;
$body-color: #fff;

body {
  margin-top: 50px;
  color: $body-color;
  background: $body-bg;
  font-family: Helvetica;
}

$color-range: $body-color;
$border-range: 2px;
$width-range: 35px;

@mixin track(){
	height: $border-range + 1;
  background: $brand-primary;
	cursor: pointer;
  transition: all .2s ease;
}
@mixin thumb() {
  width: $width-range;
  height: $width-range;
  border-radius: 100%;
  background: $body-bg;
  position: relative;
  border: $border-range solid $brand-primary;
  z-index: 3;
  cursor: pointer;
}
.range-slider{
  display: flex;
  color: $color-range;
  user-select: none;
  // display: inline-block;
  position: relative;
  padding-left: $width-range + 5;
  height: 40px;
  padding-right: $width-range + 5;
  width: 270px;
  span{
    font-size: 130%;
    cursor: pointer;
    display: inline-block;
    vertical-align: middle;
    width: $width-range - $border-range;
    height: $width-range - $border-range;
    border-radius: 50%;
    text-align: center;
    line-height: $width-range - 3;
    border: $border-range solid $brand-primary;
    position: absolute;
    top: 50%;
    transform: translatey(-50%);
    z-index: 9;
    &.left{
      line-height: $width-range - 5;
      left: 0;
    }
    &.right{
      right: 0;
      &:before{
        content: "";
        position: absolute;
        border-radius: 50%;
        left: $border-range;
        top: $border-range;
        width: $width-range - ($border-range * 3);
        height: $width-range - ($border-range * 3);
        background: $brand-primary;
        z-index: -1;
      }
    }
  }
  input{
    -webkit-appearance: none;
    display: inline-block;
    margin: 0 -5px;
    vertical-align: middle;
    width: 300px;
    height: 30px;
    background: none;
    &:focus{
      outline: none;
    }
    // webkit
    &::-webkit-slider-runnable-track{
      @include track();
    }
    &::-webkit-slider-thumb{
      -webkit-appearance:none;
      @include thumb();
      margin-top: $border-range;
      transform: translateY(-50%);
    }
    // firefox
    &::-moz-range-track{
      @include track();
    }
    &::-moz-range-thumb{
      -webkit-appearance:none;
      @include thumb();
    }
    // ie
    &::-ms-track{
      @include track();
    }
    &::-ms-thumb{
      @include thumb();
      transform: translateY(0%);
    }
  }
}
  
</style>
