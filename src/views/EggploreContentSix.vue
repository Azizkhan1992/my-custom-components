<template>
    <div class="eggplore-six-container">
        <div class="eggplore-six-content">
            <h5>Carousel</h5>
            <eggplore-carousel :slider_images="slider_images" :interval="3000"/>
        </div>
    </div>
</template>
<script>
import EggploreCarousel from './eggplore-six/EggploreCarousel.vue';
export default {
    name: 'eggplore-six',
    components:{EggploreCarousel},
    data(){
        return{
            slider_images: [
                {id: 1, name: 'img1', img: 'img5.jpg'},
                {id: 2, name: 'img2', img: 'img6.jpg'},
                {id: 3, name: 'img3', img: 'img7.jpg'}
            ]
        }
    }
}
</script>