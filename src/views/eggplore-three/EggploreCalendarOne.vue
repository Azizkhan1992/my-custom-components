<template>
  <div class="calendar-container">
    <h5>Date Picker One</h5>
    <div class="calendar-content">
      <div
        @click="calendarActive"
        :class="
          isCalendarActive
            ? 'calendar-visible-active'
            : 'calendar-visible-deactive'
        "
      >
        <span v-for="(now, idx) in now_date" :key="idx">{{ now }}</span>

        <svg
          width="16"
          height="16"
          viewBox="0 0 16 16"
          fill="currentcolor"
          xmlns="http://www.w3.org/2000/svg"
          :class="
            isCalendarActive ? 'calendar-svg-active' : 'calendar-svg-deactive'
          "
        >
          <path
            d="M15 2C15.552 2 16 2.448 16 3V15C16 15.552 15.552 16 15 16H1C0.448 16 0 15.552 0 15V3C0 2.448 0.448 2 1 2H3V0H6V2H10V0H13V2H15ZM14 14V5H2V14H14ZM4 7H6V9H4V7ZM7 7H9V9H7V7Z"
            fill="currentcolor"
          />
        </svg>
      </div>
      <div
        :class="
          isCalendarActive
            ? 'calendar-hidden-active'
            : 'calendar-hidden-deactive'
        "
      >
        <div class="calendar-hidden-header">
          <button class="left-button" @click="prevMonth">
            <svg
              width="5"
              height="8"
              viewBox="0 0 5 8"
              fill="currentcolor"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                d="M1.66497 4L4.48766 6.82269C4.75699 7.09201 4.75699 7.52868 4.48766 7.79801C4.21833 8.06733 3.78167 8.06733 3.51234 7.79801L0.201995 4.48766C-0.0673318 4.21833 -0.0673318 3.78167 0.201995 3.51234L3.51234 0.201995C3.78167 -0.0673318 4.21833 -0.0673318 4.48766 0.201995C4.75699 0.471322 4.75699 0.907988 4.48766 1.17732L1.66497 4Z"
                fill="currentcolor"
              />
            </svg>
          </button>
          <p class="now-date">
            {{ months[currentDate.getMonth()] }} {{ currentDate.getFullYear() }}
          </p>
          <button class="right-button" @click="nextMonth">
            <svg
              width="5"
              height="8"
              viewBox="0 0 5 8"
              fill="currentcolor"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                d="M3.02448 4L0.201793 1.17731C-0.067534 0.907988 -0.067534 0.471322 0.201793 0.201995C0.47112 -0.0673323 0.907786 -0.0673323 1.17711 0.201995L4.48746 3.51234C4.75678 3.78167 4.75678 4.21833 4.48746 4.48766L1.17711 7.798C0.907786 8.06733 0.47112 8.06733 0.201793 7.798C-0.067534 7.52868 -0.067534 7.09201 0.201793 6.82268L3.02448 4Z"
                fill="currentcolor"
              />
            </svg>
          </button>
        </div>
        <div class="calendar-hidden-content">
          <table class="hidden-content-items">
            <thead>
              <tr>
                <th class="calendar-days" v-for="(day, idx) in days" :key="idx">
                  <span>{{ day }}</span>
                </th>
              </tr>
            </thead>
            <tbody ref="dayItems"></tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "eggplore-calendar",
  props: {
    value: {
      type: [Date, String],
      default: () => new Date(),
    },
  },
  data() {
    return {
      isCalendarActive: false,
      now_date: [],
      month_days: [
        { name: "Yanvar", num: 31 },
        { name: "Fevral", num: 28 },
        { name: "Mart", num: 31 },
        { name: "Aprel", num: 30 },
        { name: "May", num: 31 },
        { name: "Iyun", num: 30 },
        { name: "Iyul", num: 31 },
        { name: "Avgust", num: 31 },
        { name: "Sentabr", num: 30 },
        { name: "Oktabr", num: 31 },
        { name: "Noyabr", num: 30 },
        { name: "Dekabr", num: 31 },
      ],
      days: ["Du", "Se", "Chor", "Pay", "Ju", "Shan", "Yak"],
      months: [
        "Yanvar",
        "Fevral",
        "Mart",
        "Aprel",
        "May",
        "Iyun",
        "Iyul",
        "Avgust",
        "Sentabr",
        "Oktabr",
        "Noyabr",
        "Dekabr",
      ],
      otherMonth: null,
    };
  },
  mounted() {
    this.getNowDate();
    this.getMonthDays();
  },
  computed: {
    currentDate() {
      if (this.otherMonth) {
        return this.otherMonth;
      }

      return typeof this.value == "string" ? new Date(this.value) : this.value;
    },
    firstDate() {
      return new Date(
        this.currentDate.getFullYear(),
        this.currentDate.getMonth(),
        1
      );
    },
    lastDate() {
      return new Date(
        this.currentDate.getFullYear(),
        this.currentDate.getMonth() + 1,
        0
      );
    },
    calendarRows() {
      return 35 - this.getDay(this.firstDate) < this.lastDate.getDate() ? 6 : 5;
    },
  },
  methods: {
    getMonthDays() {
      let daysContainer = this.$refs.dayItems;
      let day = 1;

      for (let x = 1; x <= this.calendarRows; x++) {
        const row = this.createElement("tr");
        for (let y = 1; y <= 7; y++) {
          const column = this.createElement("td");

          this.addEventToDay(column);

          if (
            (x == 1 && y >= this.getDay(this.firstDate)) ||
            (day <= this.lastDate.getDate() && x != 1)
          ) {
            let this_day = this.currentDate.getDate();
            if (day == this_day) {
              column.classList.add("current-day");
            }
            column.innerText = day++;
          }

          row.appendChild(column);
        }
        daysContainer.appendChild(row);
      }
    },
    isCurrentDate() {
      return this.currentDate;
    },
    getDay(day) {
      const calendarDay = day.getDay();
      return calendarDay === 0 ? 7 : calendarDay;
    },
    createElement(elName) {
      return document.createElement(elName);
    },
    getNowDate() {
      let now = new Date();
      let day = now.getDate();
      let month = now.getMonth();
      let year = now.getFullYear();
      for (let i = 0; i < this.months.length; i++) {
        if (i === month) {
          this.now_date.push(day, this.months[i], year);
        }
      }
    },
    calendarActive() {
      this.isCalendarActive = !this.isCalendarActive;
    },
    prevMonth() {
      this.changeMonth();
      this.refreshCalendar();
    },
    nextMonth() {
      this.changeMonth(true);
      this.refreshCalendar();
    },
    refreshCalendar() {
      this.$refs.dayItems.innerHTML = "";
      this.getMonthDays();
    },
    changeMonth(isNext = false) {
      const month = isNext
        ? this.currentDate.getMonth() + 1
        : this.currentDate.getMonth() - 1;

      this.otherMonth = new Date(
        this.currentDate.getFullYear(),
        month,
        this.currentDate.getDate()
      );
    },
    addEventToDay(column) {
      column.addEventListener("click", (e) => {
        column.classList.add("current-selected-day");
        let user_selected_date = new Date(
          this.currentDate.getFullYear(),
          this.currentDate.getMonth(),
          +e.target.innerText
        );
        this.now_date = [];
        let user_day = user_selected_date.getDate();
        let user_year = user_selected_date.getFullYear();
        let user_month = user_selected_date.getMonth();
        for (let i = 0; i < this.months.length; i++) {
          if (i === user_month) {
            this.now_date.push(user_day, this.months[i], user_year);
          }
        }
        this.$emit(
          "input",
          new Date(
            this.currentDate.getFullYear(),
            this.currentDate.getMonth(),
            +e.target.innerText
          )
        );
      });
    },
  },
};
</script>
<style></style>
