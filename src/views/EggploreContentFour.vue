<template>
  <div class="other-components-container">
    <h4>Other Components</h4>
    <div class="other-components-content">
      <hr />
      <div class="components-wrapper">
        <eggplore-check-boxes :options="options" :value="checkboxValues" />
        <eggplore-radio-button />
        <eggplore-switch v-model="checkbox" />
        <eggplore-tags />
        <eggplore-loading-two v-if="checkbox" />
        <eggplore-loading-one v-else />
      </div>
    </div>
  </div>
</template>
<script>
import EggploreCheckBoxes from "./eggplore-four/EggploreCheckBoxes.vue";
import EggploreRadioButton from "./eggplore-four/EggploreRadioButton.vue";
import EggploreSwitch from "./eggplore-four/EggploreSwitch.vue";
import EggploreTags from "./eggplore-four/EggploreTags.vue";
import EggploreLoadingTwo from "./eggplore-four/EggploreLoadingTwo.vue";
import EggploreLoadingOne from "./eggplore-four/EggploreLoadingOne.vue";
export default {
  name: "eggplore-content-four",
  components: {
    EggploreCheckBoxes,
    EggploreRadioButton,
    EggploreSwitch,
    EggploreTags,
    EggploreLoadingOne,
    EggploreLoadingTwo,
  },
  data() {
    return {
      checkbox: false,
      options: [
        { name: "Uzbekistan", value: "UZB" },
        { name: "Kazakhistan", value: "KZ" },
        { name: "Gijduvon", value: "Gij", disabled: true },
      ],
      checkboxValues: ["UZB"],
    };
  },
  methods: {},
};
</script>
