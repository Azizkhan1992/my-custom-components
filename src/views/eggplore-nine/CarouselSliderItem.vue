<template>
    <div class="carousel-slider-item">
        <img :src="require('@/assets/Content-nine/' + slide.img)" alt="">
    </div>
</template>
<script>
export default {
    name: 'carousel-slider-item',
    props:{
        slide:{
            type: Object,
            default: ()=> {}
        }
    }
}
</script>