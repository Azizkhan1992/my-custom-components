<template>
  <div class="eggplore-switch-container" ref="switch">
    <h5>Switch</h5>
    <div class="switch-content">
      <input
        type="checkbox"
        class="switch-checkbox"
        v-model="checked"
        @change="onChange"
      />
      <label for="checkbox" :class="checked ? 'switch-active' : 'switch-deactive'" class="switch-label">
        <svg
          width="25"
          height="24"
          viewBox="0 0 25 24"
          fill="currentcolor"
          xmlns="http://www.w3.org/2000/svg"
          :class="checked ? 'switch-svg-active' : 'switch-svg-deactive'"
          
        >
          <path
            d="M12.0869 24C18.7143 24 24.0869 18.6274 24.0869 12C24.0869 5.37258 18.7143 0 12.0869 0C5.4595 0 0.0869141 5.37258 0.0869141 12C0.0869141 18.6274 5.4595 24 12.0869 24Z"
            fill="currentcolor"
          />
        </svg>
      </label>
    </div>
  </div>
</template>
<script>
export default {
  name: "eggplore-switch",
  props: {
    defaultChecked: {
      type: Boolean,
      default: false,
    },
  },
  data() {
    return {
      checked: this.defaultChecked,
    };
  },
  methods: {
    onChange() {
        if(this.checked){
            const switch_parent = this.$refs.switch.parentElement
            switch_parent.classList.add('switch-change')
        }else{
            const switch_parent = this.$refs.switch.parentElement
            switch_parent.classList.remove('switch-change')
        }
      this.$emit("input", this.checked);
    },
  },
};
</script>
