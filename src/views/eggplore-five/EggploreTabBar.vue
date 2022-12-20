<template>
  <div class="eggplore-tabbar-container">
    <h5>Tab</h5>
    <div class="tabbar-content">
      <div class="tabbar" ref="tabChild">
        <div
          v-for="(header, idx) in tabHeaders"
          :key="idx"
          :class="header.active ? 'tab-header-active' : 'tab-header-deactive'"
        >
          <button
            :class="header.active ? 'default-active' : 'default-deactive'"
            @click="setActiveTab(header.value)"
          >
            {{ header.name }}
          </button>
          <svg
            width="47"
            height="3"
            viewBox="0 0 47 3"
            fill="currentcolor"
            xmlns="http://www.w3.org/2000/svg"
            :class="
              header.active ? 'default-svg-active' : 'default-svg-deactive'
            "
          >
            <path
              d="M0 3C0 1.34315 1.34315 0 3 0H44C45.6569 0 47 1.34315 47 3H0Z"
              fill="currentcolor"
            />
          </svg>
        </div>
      </div>
      <slot :active="activeTab" />
    </div>
  </div>
</template>
<script>
export default {
  name: "eggplore-tabbar",
  props: {
    headers: {
      type: Array,
      default: () => [],
    },
  },
  mounted() {
    this.initHeaders();
  },
  data() {
    return {
      tabHeaders: [],
    };
  },
  computed: {
    activeTab() {
      return this.tabHeaders.length > 0
        ? this.tabHeaders.find((item) => item.active).value
        : null;
    },
  },
  methods: {
    setActiveTab(tabValue) {
      this.tabHeaders = this.tabHeaders.map((item) => {
        item.active = false;

        if (item.value === tabValue) {
          item.active = true;
        }
        return item;
      });
    },
    initHeaders() {
      this.tabHeaders = this.headers.map((item) => {
        item.active = !!item.active;
        return item;
      });
    },
  },
};
</script>
