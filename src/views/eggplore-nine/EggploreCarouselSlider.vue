<template>
    <div class="carousel-slider">
        <div class="carousel-slider-inner">
            <carousel-slider-item v-for="(slide, idx) in slides" :key="`item-${idx}`" :slide="slide"></carousel-slider-item>
        </div>
    </div>
    
</template>
<script>
import CarouselSliderItem from './CarouselSliderItem.vue'
export default {
    name: 'carousel-slider-item',
    components: {CarouselSliderItem},
    props:{
        slides: {
            type: Array,
            default: ()=> []
        },
        visibleSlide: {
            type: Number,
            default: 0
        },
        interval: {
            type: Number,
            default: 0
        }
    },
    data(){
        return{
            slider: [],
            counter: 0
        }
    },
    
}
</script>
<style>
.carousel-slider{
    display: flex;
    justify-content: center;
}
.carousel-slider-inner{
    position: relative;
    display: flex;
    flex-direction: row;
    width: 980px;
    height: 320px;
    overflow: hidden;
}
</style>