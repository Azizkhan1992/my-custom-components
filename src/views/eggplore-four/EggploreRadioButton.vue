<template>
    <div class="radio-button-container">
        <h5>Radio Button</h5>
        <div class="radio-button-content">
            <input type="radio" value="male" v-model="gender" checked>
            <input type="radio" value="female" v-model="gender">
            <h6>{{gender}}</h6>
        </div>
    </div>
</template>
<script>
export default {
    name: 'eggplore-radio-button',
    data(){
        return{
            gender: 'male'
        }
    },
    
}
</script>