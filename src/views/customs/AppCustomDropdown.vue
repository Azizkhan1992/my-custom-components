<template>
    <div class="custom-dropdown-container">
        <h5>Custom Dropdown</h5>
        <div class="custom-dropdown-content">
            <div class="custom-visible-part" @click="dropdownActive">
                {{dropdown_item.name}}
            </div>
            <div :class="isDropdownActive ? 'custom-hidden-active' : 'custom-hidden-deactive'">
                <div class="custom-selected-item" v-for="(drop, idx) in dropdown" :key="idx" @click="dropdownItemSelect(drop)">
                    {{drop.name}}
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: 'custom-dropdown',
    data(){
        return{
            dropdown: [],
            send_item: [],
            dropdown_item: {id: 1, name: 'Kompyuter', value: 'Komp'},
            isDropdownActive: false
        }
    },
    props:{
        value:{
            type: Array,
            default: ()=> []
        }
    },
    mounted(){
        this.dropdownValue()
    },
    methods:{
        dropdownActive(){
            this.isDropdownActive = !this.isDropdownActive
        },
        dropdownItemSelect(e){
            this.send_item.push(e)
            this.$emit('input', this.send_item)
        },
        dropdownValue(){
            this.dropdown = this.value
        }
    }

}
</script>