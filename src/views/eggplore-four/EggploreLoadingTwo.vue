<template>
  <div class="eggplore-loading-container">
    <h5>Loading Two</h5>
    <div class="loading-content">
        <input type="number" v-model="processing">
        <span :class="processing ? 'loading-span-active' : 'loading-span-deactive'">{{processing}}</span>
      <progress id="file" :value="processing" min="0" max="100"
      ></progress>
    </div>
  </div>
</template>
<script>
export default {
  name: "eggplore-loading",
  data(){
    return{
        processing: null
    }
  }
};
</script>
