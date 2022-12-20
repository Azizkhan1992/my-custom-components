<template>
  <div class="second-box-container">
    <h5>Checkbox Second</h5>
    <div class="second-box-content">
      <div
        class="second-box-wrapper"
        v-for="(province, idx) in provinces_box"
        :key="idx"
        ref="boxWrapper"
      >
        <input
          type="checkbox"
          v-model="selected_provinces"
          :value="province"
          :disabled="province.disabled"
          class="input-all-deactive"
          :ref="`checkProvince-${province.value}`"
          @change="itemChange(province)"
        />
        <label for="checkbox">{{ province.name }}</label>
      </div>
      <div class="all-input-block">
        <input
          type="checkbox"
          class="all-deactive"
          @change="setAll"
          ref="allInput"
        />
        <label for="checkbox">All</label>
      </div>
    </div>
  </div>
</template>
<script>

export default {
  name: "second-checkbox",
  data() {
    return {
      isAllActive: false,
      provinces_box: [
        { name: "Andijon", value: "And" },
        { name: "Buxoro", value: "Bux" },
        { name: "Farg'ona", value: "Far" },
        { name: "Jizzax", value: "Jiz" },
        { name: "Namangan", value: "Nam" },
        { name: "Navoiy", value: "Nav" },
        { name: "Qashqadaryo", value: "Qash" },
        { name: "Samarqand", value: "Sam" },
        { name: "Sirdaryo", value: "Sir" },
        { name: "Surxondaryo", value: "Sur" },
        { name: "Toshkent", value: "Tosh" },
        { name: "Xorazm", value: "Xor" },
        { name: "Toshkent Shahar", value: "G'ij", disabled: true },
      ],
      selected_provinces: [],
    };
  },
  props: {
    provinces: {
      type: Array,
      default: () => [],
    },
  },
  methods: {
    itemChange(e) {
      if (this.selected_provinces.find((elem) => elem.value == e.value)) {
        let input_item = this.$refs[`checkProvince-${e.value}`];
        input_item.forEach((elem) => {
          elem.classList.remove("input-all-deactive");
          elem.classList.remove("input-item-deactive");
          elem.classList.add("input-item-active");
        });
      } else {
        let input_item = this.$refs[`checkProvince-${e.value}`];
        input_item.forEach((elem) => {
          elem.classList.remove("input-item-active");
          elem.classList.add("input-item-deactive");
        });
        let all_input = this.$refs.allInput;
        all_input.classList.remove("all-item-active");
        all_input.classList.remove("all-active");
        all_input.classList.add("all-deactive");
        console.log(all_input);
      }
    },
    checkSelected(e) {
      if (e) {
        if (e.length == 12) {
          let all_input = this.$refs.allInput;
          all_input.classList.add("all-active");
        } else {
          if (e.length > 0) {
            let all_input = this.$refs.allInput;
            all_input.classList.remove("all-deactive");
            all_input.classList.add("all-item-active");
          } else {
            let all_input = this.$refs.allInput;
            all_input.classList.remove("all-item-active");
            all_input.classList.add("all-deactive");
          }
        }
      }
    },
    setAll() {
      if (this.selected_provinces.length === 0) {
        this.selected_provinces = this.provinces_box;
        let remove_class = this.$refs.allInput;
        remove_class.classList.remove("all-item-active");
        remove_class.classList.add("all-active");

        this.provinces_box.forEach((elem) => {
          let set_all_active = this.$refs[`checkProvince-${elem.value}`];
          set_all_active.forEach((item) => {
            if (item.disabled) {
                // console.log(item)
            } else {
              item.classList.add("input-all-active");
            }
          });
        });
      } else {
        this.selected_provinces = [];

        let remove_class = this.$refs.allInput;
        remove_class.classList.remove("all-active");
        remove_class.classList.add("all-item-active");

        this.provinces_box.forEach((elem) => {
          let set_all_active = this.$refs[`checkProvince-${elem.value}`];
          set_all_active.forEach((item) => {
            if (item.disabled) {
                // console.log(item)
            } else {
              item.classList.remove("input-all-active");
              item.classList.remove("all-item-active");
              item.classList.add("all-deactive");
            }
          });
        });
      }
    },
  },
  watch: {
    selected_provinces: function (val) {
      this.checkSelected(val);
    },
  },
};
</script>
