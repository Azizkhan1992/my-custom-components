<template>
    <div class="eggplore-seven-container">
        <h5>Owl Carousel</h5>
        <div class="eggplore-seven-content">
            <carousel @next="next" @prev="prev">
                <carousel-slide v-for="(slide, idx) in slides" :key="slide" :index="idx" :visibleSlide="visibleSlide" :direction="direction">
                    <img :src="require('@/assets/Content-six/' + slide)"/>
                </carousel-slide>
            </carousel>
        </div>
    </div>
</template>
<script>
import Carousel from './eggplore-seven/Carousel.vue';
import CarouselSlide from './eggplore-seven/CarouselSlide.vue';
export default {
    name: 'eggplore-seven',
    components: {Carousel, CarouselSlide},
    data(){
        return{
            slides: [
                'img5.jpg',
                'img6.jpg',
                'img7.jpg'
            ],
            visibleSlide: 0,
            direction: 'left'
        }
    },
    computed:{
        sliderLen(){
            return this.slides.length
        }
    },
    methods:{
        next(){
            if(this.visibleSlide>= this.sliderLen-1){
                this.visibleSlide= 0
            }else{
                this.visibleSlide++
            }
            this.direction = 'left'
        },
        prev(){
            if(this.visibleSlide <= 0){
                this.visibleSlide = this.sliderLen-1
            }else{
                this.visibleSlide-- 
            }
            this.direction = 'right'
        }
    }
}
</script>