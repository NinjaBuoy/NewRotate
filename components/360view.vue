<template>
  <div class="view-360">
    <VueProductSpinner
      :images="imagesActive"
      :slider="true"
      :infinite="false"
      :speed="10"
      sliderClass="custom-range"
    >
    </VueProductSpinner>
  </div>
</template>
<script>
import VueProductSpinner from "./VueProductSpinner";
// import RoundSlider from "vue-round-slider";

export default {
  components: {
    VueProductSpinner,
    // RoundSlider,
  },
  data() {
    return {
      sliderValue: 60,
      imagesActive: [],
      imageCount: "98",
    };
  },
  methods: {
    async input() {
      for (var i = 0; i <= this.imageCount; i++) {
        var push = `images/${i}.png`;
        this.imagesActive.push(push);
      }
    },
  },
  created() {
    this.input();
  },
};
</script>

<style lang="scss">
.view-360 {
  height: 96vh;
  /* background: linear-gradient(to right top, #65dfc9, #6cdbeb); */
  background: linear-gradient(
    to right bottom,
    rgba(255, 255, 255, 0.7),
    rgba(255, 255, 255, 0.3)
  );
  backdrop-filter: blur(2rem);
}
.view-360:focus {
  outline: none;
}
.vue-product-spinner {
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  height: 100%;
  position: relative;
}
.vue-product-spinner:focus {
  outline: none;
}
.view-360 img {
  width: 100%;
  position: relative;
  object-fit: cover;
}
.view-360 img:focus {
  outline: none !important;
  border: none;
}
.view-360 input {
  max-width: 300px;
  position: absolute;
  bottom: 15%;
  background: none;
}
.rs-chrome {
  margin: 20px auto;
}

input[type="range"] {
  appearance: none;
  padding: 0;
  width: 100%;
  height: 22px;
  cursor: pointer;
  display: block;
}
input[type="range"]:focus {
  outline: none;
}
input[type="range"][disabled] {
  opacity: 0.3;
  cursor: default;
}

input::-webkit-slider-runnable-track {
  box-sizing: border-box;
  width: 100%;
  height: 4px;
  background: #ffffff;
  border-radius: 100px;
  margin: 11px 0;
}
input::-moz-range-track {
  box-sizing: border-box;
  width: 100%;
  height: 4px;
  background: #e6e6e6;
  border-radius: 100px;
  margin: 11px 0;
}
input::-ms-track {
  box-sizing: border-box;
  width: 100%;
  height: 4px;
  background: #e6e6e6;
  border-radius: 100px;
  color: transparent;
  padding: 11px 0;
  background: transparent;
  border-color: transparent;
}
input::-ms-fill-lower,
input::-ms-fill-upper {
  box-sizing: border-box;
  width: 100%;
  height: 4px;
  background: #e6e6e6;
  border-radius: 100px;
}
input::-ms-fill-lower {
  background: #ffffff;
}

input::-webkit-slider-thumb {
  box-sizing: border-box;
  box-shadow: 0px 4px 25px rgba(0, 0, 0, 0.5);
  border: 6px solid #fff;
  height: 24px;
  width: 24px;
  border-radius: 100px;
  background: #333940;
  cursor: pointer;
  appearance: none;
  // transform: translateY(-50%);
  transform: translateY(-50%);
  margin-top: 2px;
}
input::-moz-range-thumb {
  box-sizing: border-box;
  box-shadow: 0px 4px 25px rgba(0, 0, 0, 0.5);
  border: 6px solid #fff;
  height: 24px;
  width: 24px;
  border-radius: 100px;
  background: #333940;
  cursor: pointer;
}
input::-ms-thumb {
  box-sizing: border-box;
  box-shadow: 0px 4px 25px rgba(0, 0, 0, 0.5);
  border: 6px solid #fff;
  height: 24px;
  width: 24px;
  border-radius: 100px;
  background: #333940;
  cursor: pointer;
}
</style>
