<template>
  <div class="calendar-two-container">
    <h5>Date Picker Two</h5>
    <div class="calendar-two-content" @click="calendarInputActive">
      <input
        type="date"
        id="start"
        name="trip-start"
        :class="isCalendarInput ? 'input-active' : 'input-deactive'"
        value="date"
      />
    </div>
  </div>
</template>
<script>
export default {
  name: "eggplore-picker-two",
  data() {
    return {
      isCalendarInput: false,
      date: new Date(),
    };
  },
  mounted() {
    this.getSelectDate();
  },
  methods: {
    calendarInputActive() {
      this.isCalendarInput = !this.isCalendarInput;
    },
  },
};
</script>
<style></style>
