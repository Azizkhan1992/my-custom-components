<template>
  <div>
    <h5>Direction Form</h5>
    <div class="direction-container">
      <div :class="isPathButton ? 'search-location' : 'own-location'">
        <div class="own-location-block">
          <svg
            width="16"
            height="16"
            viewBox="0 0 16 16"
            fill="currentcolor"
            xmlns="http://www.w3.org/2000/svg"
            class="own-location-svg"
          >
            <path
              d="M0.768857 4.04917L14.596 0.098548C15.3861 -0.0989828 16.0775 0.592375 15.88 1.3825L11.9294 15.2097C11.6331 16.0985 10.4479 16.1973 10.0528 15.3084L7.28738 8.78991L0.768857 6.02447C-0.218798 5.53065 -0.120031 4.34546 0.768857 4.04917Z"
              fill="currentcolor"
            />
          </svg>
          {{ own_location }}
        </div>
      </div>

      <div class="direction-dot-loader">
        <div :class="search_direction ? 'dot-fire' : 'dot-not-fire'">
          <span></span>
          <span></span>
          <span></span>
        </div>
      </div>

      <svg
        width="32"
        height="32"
        viewBox="0 0 32 32"
        fill="currentcolor"
        xmlns="http://www.w3.org/2000/svg"
        :class="isPathButton ? 'change-path-active' : 'change-path-deactive'"
        @click="changePath"
      >
        <path
          d="M16 32C24.8366 32 32 24.8366 32 16C32 7.16344 24.8366 0 16 0C7.16344 0 0 7.16344 0 16C0 24.8366 7.16344 32 16 32Z"
          fill="currentcolor"
        />
        <path
          d="M16.7794 20.4062H19.0938C19.508 20.4062 19.8438 20.742 19.8438 21.1562C19.8438 21.5705 19.508 21.9062 19.0938 21.9062H14.9688C14.5545 21.9062 14.2188 21.5705 14.2188 21.1562V17.0312C14.2188 16.617 14.5545 16.2812 14.9688 16.2812C15.383 16.2812 15.7188 16.617 15.7188 17.0312V19.3456L20.6259 14.4384C20.9188 14.1455 21.3937 14.1455 21.6866 14.4384C21.9795 14.7313 21.9795 15.2062 21.6866 15.4991L16.7794 20.4062ZM15.2206 11.5938H12.9062C12.492 11.5938 12.1562 11.258 12.1562 10.8438C12.1562 10.4295 12.492 10.0938 12.9062 10.0938H17.0312C17.4455 10.0938 17.7812 10.4295 17.7812 10.8438V14.9688C17.7812 15.383 17.4455 15.7188 17.0312 15.7188C16.617 15.7188 16.2812 15.383 16.2812 14.9688V12.6544L11.3741 17.5616C11.0812 17.8545 10.6063 17.8545 10.3134 17.5616C10.0205 17.2687 10.0205 16.7938 10.3134 16.5009L15.2206 11.5938Z"
          fill="currentcolor"
          class="svg-path"
        />
      </svg>

      <div :class="isPathButton ? 'own-location' : 'search-location'">
        <div class="search-location-block">
          <svg
            width="16"
            height="18"
            viewBox="0 0 16 18"
            fill="currentcolor"
            xmlns="http://www.w3.org/2000/svg"
            :class="
              search_direction
                ? 'search-direction-active'
                : 'search-direction-deactive'
            "
          >
            <path
              d="M8.00344 0C4.55996 0 0.959961 2.66087 0.959961 7.04348C0.959961 11.1913 7.22083 17.5304 7.45561 17.7652C7.61213 17.9217 7.76866 18 8.00344 18C8.23822 18 8.39474 17.9217 8.55126 17.7652C8.78605 17.5304 15.0469 11.1913 15.0469 7.04348C15.0469 2.66087 11.4469 0 8.00344 0ZM8.00344 9.3913C6.673 9.3913 5.65561 8.37391 5.65561 7.04348C5.65561 5.71304 6.673 4.69565 8.00344 4.69565C9.33387 4.69565 10.3513 5.71304 10.3513 7.04348C10.3513 8.37391 9.33387 9.3913 8.00344 9.3913Z"
              fill="currentcolor"
            />
            <defs>
              <linearGradient
                id="paint0_linear_72967_235"
                x1="8.00344"
                y1="-9"
                x2="-9.46901"
                y2="4.67409"
                gradientUnits="userSpaceOnUse"
              >
                <stop stop-color="#BD7AE3" />
                <stop offset="1" stop-color="#8461C9" />
              </linearGradient>
            </defs>
          </svg>

          <input
            type="text"
            class="search-location-input"
            placeholder="Enter destination..."
            v-model="search_direction"
          />

          <svg
            width="12"
            height="12"
            viewBox="0 0 12 12"
            fill="currentcolor"
            xmlns="http://www.w3.org/2000/svg"
            @click="deleteSearchDirection"
            :class="
              search_direction
                ? 'delete-search-active'
                : 'delete-search-deactive'
            "
          >
            <path
              d="M6 0C2.7 0 0 2.7 0 6C0 9.3 2.7 12 6 12C9.3 12 12 9.3 12 6C12 2.7 9.3 0 6 0ZM8.625 7.575L7.575 8.625L6 7.05L4.425 8.625L3.375 7.575L4.95 6L3.375 4.425L4.425 3.375L6 4.95L7.575 3.375L8.625 4.425L7.05 6L8.625 7.575Z"
              fill="currentcolor"
            />
          </svg>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "eggplore-location",
  data() {
    return {
      own_location: "Your location",
      isPathDirection: false,
      isPathButton: false,
      search_direction: null,
    };
  },
  methods: {
    changePath() {
      this.isPathButton = !this.isPathButton;
    },
    deleteSearchDirection() {
      this.search_direction = null;
    },
  },
};
</script>
<style></style>
