<template>
  <div class="loading-one-container">
    <h5>Loading One</h5>
    <div class="loading-one-content">
      <input type="number" v-model="percentage" min="0" max="100" />
      <span
        v-if="isShowPercent"
        :class="isShowPercent ? 'percent-show-active' : 'percent-show-deactive'"
        >Done
        <svg
          width="10"
          height="8"
          viewBox="0 0 10 8"
          fill="currentcolor"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M8.49373 0.758435C8.83831 0.413855 9.39698 0.413855 9.74156 0.758435C10.0861 1.10302 10.0861 1.66169 9.74156 2.00627L4.44745 7.30039C4.10287 7.64497 3.54419 7.64497 3.19961 7.30039L0.258435 4.35921C-0.0861451 4.01463 -0.0861451 3.45596 0.258435 3.11138C0.603015 2.7668 1.16169 2.7668 1.50627 3.11138L3.82353 5.42863L8.49373 0.758435Z"
            fill="currentcolor"
          />
        </svg>
      </span>
      <span
        v-else
        :class="style_percent ? 'percent-span-active' : 'percent-span-deactive'"
        >{{ style_percent }}</span
      >

      <div class="show-loading">
        <div class="show-percentage" :style="{ width: style_percent + '%' }"></div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "loading-one",
  data() {
    return {
      percentage: 0,
      style_percent: 0,
      isShowPercent: false,
    };
  },
  methods: {
    loadingChange(e) {
      if (e == 100) {
        this.style_percent = e
        this.isShowPercent = true;
      }
      else{
        this.style_percent = e
        this.isShowPercent = false
      }
    },
  },
  watch:{
    'percentage' : function(val){
      if(val>=100){
        this.loadingChange(100)
      }else if(val<=0){
        this.loadingChange(0)
      }else{
        this.loadingChange(this.percentage)
      }
    }
  }
};
</script>
