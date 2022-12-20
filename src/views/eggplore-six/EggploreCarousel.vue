<template>
  <div class="carousel-container">
    <div class="carousel-content">
      <div
        class="carousel-wrapper"
        :style="{ 'margin-left': '-' + 900 * currentSlideIndex + 'px' }"
      >
        <eggplore-carousel-item
          v-for="(image, idx) in slider_images"
          :key="idx"
          :image_item="image"
          :image_slide="true"
          :width="2700"
        >
          <p>{{ image.name }}</p>
          <p>{{ image.id }}</p>
        </eggplore-carousel-item>
      </div>
      
    </div>
    <div class="carousel-btn">
        <button @click="prevSlide">Prev</button>
      <button @click="nextSlide">Next</button>
    </div>
    
  </div>
</template>
<script>
import EggploreCarouselItem from "./EggploreCarouselItem.vue";
export default {
  name: "eggplore-carousel",
  components: { EggploreCarouselItem },
  data() {
    return {
      currentSlideIndex: 0,
    };
  },
  props: {
    slider_images: {
      type: Array,
      default: () => [],
    },
    interval: {
      type: Number,
      default: 0,
    },
  },
  mounted() {
    if (this.interval > 0) {
      let vm = this;
      setInterval(() => {
        vm.nextSlide();
      }, vm.interval);
    }
  },
  methods: {
    prevSlide() {
      if (this.currentSlideIndex > 0) {
        this.currentSlideIndex--;
      }
    },
    nextSlide() {
      if (this.currentSlideIndex >= this.slider_images.length - 1) {
        this.currentSlideIndex = 0;
      } else {
        this.currentSlideIndex++;
      }
    },
  },
};
</script>
