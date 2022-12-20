<template>
  <div class="input-forms-container">
    <h4>Input Forms</h4>
    <div class="input-forms">
      <hr />
      <div class="input-forms-wrapper">
        <div class="input-default">
          <h5>Default</h5>
          <input
            type="text"
            class="default-input-one"
            placeholder="Placeholder"
          />
        </div>
        <div class="input-password">
          <h5>Password</h5>
          <div class="input-svg-one">
            <input
              :type="isShowPassword ? 'text' : 'password'"
              class="password-input-one"
              autocomplete="new new-password"
              placeholder="Password"
            />
            <svg
              width="16"
              height="12"
              viewBox="0 0 16 12"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
              class="svg-one"
              @click="showPassword"
            >
              <path
                d="M8 0.36377C4.36364 0.36377 1.25818 2.62559 0 5.81832C1.25818 9.01104 4.36364 11.2729 8 11.2729C11.6364 11.2729 14.7418 9.01104 16 5.81832C14.7418 2.62559 11.6364 0.36377 8 0.36377ZM8 9.45468C5.99273 9.45468 4.36364 7.82559 4.36364 5.81832C4.36364 3.81104 5.99273 2.18195 8 2.18195C10.0073 2.18195 11.6364 3.81104 11.6364 5.81832C11.6364 7.82559 10.0073 9.45468 8 9.45468ZM8 3.6365C6.79273 3.6365 5.81818 4.61104 5.81818 5.81832C5.81818 7.02559 6.79273 8.00013 8 8.00013C9.20727 8.00013 10.1818 7.02559 10.1818 5.81832C10.1818 4.61104 9.20727 3.6365 8 3.6365Z"
                fill="currentcolor"
              />
            </svg>
          </div>
        </div>
        <div class="left-icon">
          <h5>Left Icon</h5>
          <div class="input-svg-two">
            <input
              type="text"
              class="left-input"
              placeholder="Placeholder"
              v-model="Input_Icon"
            />
            <svg
              width="12"
              height="14"
              viewBox="0 0 12 14"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
              class="svg-two"
              :class="Input_Icon ? 'active-svg' : 'deactive-svg'"
            >
              <path
                d="M6 0.259766C2.65714 0.259766 0 2.91691 0 6.25977C0 7.88834 0.6 9.43119 1.8 10.5455C1.88571 10.6312 5.31429 13.7169 5.4 13.8026C5.74286 14.0598 6.25714 14.0598 6.51429 13.8026C6.6 13.7169 10.1143 10.6312 10.1143 10.5455C11.3143 9.43119 11.9143 7.88834 11.9143 6.25977C12 2.91691 9.34286 0.259766 6 0.259766ZM6 7.97405C5.05714 7.97405 4.28571 7.20262 4.28571 6.25977C4.28571 5.31691 5.05714 4.54548 6 4.54548C6.94286 4.54548 7.71429 5.31691 7.71429 6.25977C7.71429 7.20262 6.94286 7.97405 6 7.97405Z"
                fill="currentcolor"
              />
            </svg>
          </div>
        </div>
        <div @click="changeActiveClass" class="input-dropdown">
          <h5>Dropdown</h5>
          <div class="dropdown-blog">
            <div @click="checkActive" class="visible-part">
              {{ default_value.text }}
              <svg
                width="10"
                height="7"
                viewBox="0 0 10 7"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
                :class="
                  isDropdownActive ? 'svg-three-active' : 'svg-three-deactive'
                "
              >
                <path
                  d="M0.41506 1.65079L4.24084 6.1142C4.60026 6.53353 5.23156 6.58209 5.65089 6.22267C5.68977 6.18934 5.72603 6.15308 5.75935 6.1142L9.58513 1.65079C9.94455 1.23147 9.89599 0.600166 9.47667 0.240743C9.29542 0.0853922 9.06459 0 8.82587 0L1.17432 0C0.622032 0 0.174316 0.447715 0.174316 1C0.174316 1.23871 0.259709 1.46955 0.41506 1.65079Z"
                  fill="currentcolor"
                />
              </svg>
              <div :class="isClockActive ? 'active-clock' : 'deactive-clock'">
                <svg
                  width="12"
                  height="12"
                  viewBox="0 0 12 12"
                  fill="none"
                  xmlns="http://www.w3.org/2000/svg"
                  :class="
                    isDropdownActive ? 'svg-four-active' : 'svg-four-deactive'
                  "
                >
                  <path
                    d="M6 0C2.7 0 0 2.7 0 6C0 9.3 2.7 12 6 12C9.3 12 12 9.3 12 6C12 2.7 9.3 0 6 0ZM9 6.75H5.25V3H6.75V5.25H9V6.75Z"
                    fill="currentcolor"
                  />
                </svg>
              </div>
            </div>
            <div
              :class="
                isDropdownActive ? 'dropdown-active' : 'dropdown-deactive'
              "
              class="hidden-part"
            >
              <div class="select-item" v-for="value in values" :key="value.id">
                <span @click="changeEvent(value)">{{ value.text }}</span>
              </div>
            </div>
          </div>
        </div>
        <div class="input-multi-select">
          <h5>Multi-Select</h5>
          <div class="multi-select-wrapper">
            <div @click="multiActive" class="multi-visible-part">
              <div
                :class="
                  isMultiInput
                    ? 'show-selected-active'
                    : 'show-selected-deactive'
                "
                v-for="(defaults, idx) in default_multi_value"
                :key="idx"
              >
                {{ defaults.text }}
                <svg
                  width="12"
                  height="12"
                  viewBox="0 0 12 12"
                  fill="currentcolor"
                  xmlns="http://www.w3.org/2000/svg"
                  :class="
                    defaults.value ? 'multi-active-svg' : 'multi-deactive-svg'
                  "
                  @click.stop="deleteItem(defaults)"
                >
                  <path
                    d="M6 0C2.7 0 0 2.7 0 6C0 9.3 2.7 12 6 12C9.3 12 12 9.3 12 6C12 2.7 9.3 0 6 0ZM8.625 7.575L7.575 8.625L6 7.05L4.425 8.625L3.375 7.575L4.95 6L3.375 4.425L4.425 3.375L6 4.95L7.575 3.375L8.625 4.425L7.05 6L8.625 7.575Z"
                    fill="currentcolor"
                  />
                </svg>
              </div>

              <svg
                width="10"
                height="7"
                viewBox="0 0 10 7"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
                :class="isMultiActive ? 'svg-five-active' : 'svg-five-deactive'"
              >
                <path
                  d="M0.41506 1.65079L4.24084 6.1142C4.60026 6.53353 5.23156 6.58209 5.65089 6.22267C5.68977 6.18934 5.72603 6.15308 5.75935 6.1142L9.58513 1.65079C9.94455 1.23147 9.89599 0.600166 9.47667 0.240743C9.29542 0.0853922 9.06459 0 8.82587 0L1.17432 0C0.622032 0 0.174316 0.447715 0.174316 1C0.174316 1.23871 0.259709 1.46955 0.41506 1.65079Z"
                  fill="currentcolor"
                />
              </svg>
            </div>
            <div
              :class="
                isMultiActive ? 'multi-hidden-active' : 'multi-hidden-deactive'
              "
            >
              <div
                class="multi-select"
                v-for="multi in multiValues"
                :key="multi.id"
              >
                <span @click="inputMultiValue(multi)">{{ multi.text }}</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "eggplore-content-two",
  data() {
    return {
      isShowPassword: false,
      isMultiActive: false,
      isDropdownActive: false,
      Input_Icon: "",
      isInput: false,
      isClockActive: false,
      isMultiInput: false,
      default_value: { text: "Value1", id: 1 },
      default_multi_value: [{ text: "Enter the keyword", id: 1 }],
      selected_multi_values: [],
      multiValues: [
        { text: "Multi Value1", id: 1, value: "active" },
        { text: "Multi Value2", id: 2 },
        { text: "Multi Value3", id: 3 },
        { text: "Multi Value4", id: 4 },
        { text: "Multi Value5", id: 5 },
      ],
      values: [
        { text: "Value1", id: 1 },
        { text: "Value2", id: 2 },
        { text: "Value3", id: 3 },
      ],
    };
  },
  methods: {
    deleteItem(item) {
      if (this.selected_multi_values.length) {
        let index = this.selected_multi_values.indexOf(item);
        console.log(index);
        this.selected_multi_values.splice(index, 1);
      }
    },
    showPassword() {
      this.isShowPassword = !this.isShowPassword;
    },
    inputMultiValue(e) {
      if (this.selected_multi_values.includes(e)) {
        this.selected_multi_values = this.selected_multi_values.filter(
          (item) => item !== e
        );
      } else {
        this.selected_multi_values.push(e);
      }

      if (this.selected_multi_values.length > 0) {
        this.isMultiInput = true;
        this.default_multi_value = this.selected_multi_values;
      } else {
        this.default_multi_value = this.selected_multi_values = [];
      }
    },
    multiActive() {
      this.isMultiActive = !this.isMultiActive;
    },
    checkActive() {
      this.isDropdownActive = !this.isDropdownActive;
      this.isClockActive = !this.isClockActive;
    },
    changeActiveClass() {
      setTimeout(() => {
        this.isClockActive = false;
      }, 1500);
    },
    changeEvent(e) {
      this.default_value = e;
    },
  },
};
</script>
<style></style>
