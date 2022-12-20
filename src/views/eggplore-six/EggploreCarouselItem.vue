<template>
    <div class="carousel-item-container" :style="{'max-width': width + 'px'}">
        <img :src="require('@/assets/Content-six/' + image_item.img)" alt="" v-if="image_slide">
        <div class="carousel-title" v-else>
            <slot/>
        </div>
    </div>
</template>
<script>
export default {
    name: 'carousel-item',
    props:{
        image_item: {
            type: Object,
            default: ()=> {}
        },
        image_slide: {
            type: Boolean,
            default: true
        },
        width:{
            type: Number,
            default: 900
        }
    }
}
</script>