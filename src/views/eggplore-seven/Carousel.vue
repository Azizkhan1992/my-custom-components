<template>
    <div class="owl-carousel-container">
        <slot></slot>

        <button @click="next" class="next">Next</button>
        <button @click="prev" class="prev">Prev</button>
    </div>
</template>
<script>
export default {
    name: 'owl-carousel',

    methods:{
        next(){
            this.$emit('next')
        },
        prev(){
            this.$emit('prev')
        }
    }
}
</script>