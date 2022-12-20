<template>
  <div class="eggplore-slider-container">
    <h5>Slider</h5>
    <div class="slider-content">
      <span>{{ slider_value }}</span>
      <div class="slider-back-part">
        <input
          type="range"
          min="0"
          max="10000"
          step="50"
          :style="{ 'background-size': slider_value / 100 + '%' }"
          v-model="slider_value"
          @change="getSliderValue"
        />
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "eggplore-slider",
  data() {
    return {
      slider_value: 0,
    };
  },
  methods: {
    getSliderValue() {
      console.log(this.slider_value);
    },
  },
};
</script>
