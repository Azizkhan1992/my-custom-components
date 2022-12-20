<template>
  <div class="eggplore-eight-container">
    <h4>Custom Components</h4>
    <div class="eggplore-eight-content">
      <hr />
      <div class="eggplore-custom-wrapper">
        <app-inc-dec v-model="count" />
        <app-custom-dropdown v-model="custom_dropdown"/>
      </div>
    </div>
  </div>
</template>
<script>
import AppIncDec from './customs/AppIncDec.vue';
import AppCustomDropdown from './customs/AppCustomDropdown.vue';
export default {
  name: "custom-component",
  components: { AppIncDec, AppCustomDropdown },
  data() {
    return {
      count: 5,
      custom_dropdown: [
        {id: 1, name: 'Kompyuter', value: 'Komp'},
        {id: 2, name: 'Telefon', value: 'Phone'},
        {id: 3, name: 'TV', value: 'Tv'},
        {id: 4, name: 'Audio', value: 'Audio'},
        {id: 5, name: 'Foto', value: 'Photo'}
      ]
    };
  },
  watch: {
    custom_dropdown: function (val) {
      console.log(val);
    },
  },
};
</script>
