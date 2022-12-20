<template>
  <div class="tag-container">
    <h5>Tags</h5>
    <div class="tag-content">
      <div class="input-tag" v-for="(tag, idx) in tags" :key="'tag' + idx">
        {{ tag }}

        <svg
          width="12"
          height="12"
          viewBox="0 0 12 12"
          fill="currentcolor"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M6 0C2.7 0 0 2.7 0 6C0 9.3 2.7 12 6 12C9.3 12 12 9.3 12 6C12 2.7 9.3 0 6 0ZM8.625 7.575L7.575 8.625L6 7.05L4.425 8.625L3.375 7.575L4.95 6L3.375 4.425L4.425 3.375L6 4.95L7.575 3.375L8.625 4.425L7.05 6L8.625 7.575Z"
            fill="currentcolor"
          />
        </svg>
      </div>
      <input type="text" @keyup.enter="addTag" v-model="tag_value" />
    </div>
  </div>
</template>
<script>
export default {
  name: "eggplore-tags",
  data() {
    return {
      tag_value: null,
      tags: [],
    };
  },
  methods: {
    addTag() {
      // console.log(this.tag_value)
      if (this.tag_value) {
        this.tags.push(this.tag_value);
      }
      this.tag_value = null;
    },
    removeTag(index) {
      this.tags.slice(index, 1);
      console.log(index);
    },
  },
};
</script>
