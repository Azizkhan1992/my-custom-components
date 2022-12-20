<template>
  <div class="content-one-container">
    <h2>Components</h2>
    <div class="content-one-content">
      <h3>Buttons</h3>
      <hr />
      <div class="content-one-buttons">
        <div class="button-blog-one common">
          <h5>Large Buttons</h5>
          <button class="blog-button-one">Default</button>
          <button class="blog-button-two">Ghost</button>
          <button class="blog-button-three">
            <svg
              width="14"
              height="14"
              viewBox="0 0 14 14"
              fill="currentcolor"
              xmlns="http://www.w3.org/2000/svg"
              class="svg-three"
            >
              <path
                d="M7 0C3.15 0 0 3.15 0 7C0 10.85 3.15 14 7 14C10.85 14 14 10.85 14 7C14 3.15 10.85 0 7 0ZM10.5 7.875H7.875V10.5H6.125V7.875H3.5V6.125H6.125V3.5H7.875V6.125H10.5V7.875Z"
                fill="currentcolor"
              />
            </svg>
            Left icon
          </button>
        </div>
        <div class="button-blog-two common">
          <h5>Small buttons</h5>
          <button class="blog-button-four">Small Default</button>
          <button class="blog-button-five">Small Ghost</button>
          <button class="blog-button-six">
            <svg
              width="14"
              height="14"
              viewBox="0 0 14 14"
              fill="currentcolor"
              xmlns="http://www.w3.org/2000/svg"
              class="svg-six"
            >
              <path
                d="M7 0C3.15 0 0 3.15 0 7C0 10.85 3.15 14 7 14C10.85 14 14 10.85 14 7C14 3.15 10.85 0 7 0ZM10.5 7.875H7.875V10.5H6.125V7.875H3.5V6.125H6.125V3.5H7.875V6.125H10.5V7.875Z"
                fill="currentcolor"
              />
            </svg>
            Small Icon
          </button>
        </div>
        <div class="button-blog-three">
          <h5>Other buttons</h5>
          <div class="wrapper-buttons">
            <button class="svg-button">
              <svg
                width="24"
                height="24"
                viewBox="0 0 24 24"
                fill="currentcolor"
                xmlns="http://www.w3.org/2000/svg"
                class="svg-seven"
              >
                <path
                  d="M3.76886 9.04941L17.596 5.09879C18.3861 4.90126 19.0775 5.59262 18.88 6.38274L14.9294 20.2099C14.6331 21.0988 13.4479 21.1976 13.0528 20.3087L10.2874 13.7901L3.76886 11.0247C2.7812 10.5309 2.87997 9.34571 3.76886 9.04941Z"
                  fill="currentcolor"
                />
              </svg>
            </button>
            <div class="other-left-btn">
              <button class="circle-btn">
                <div class="circle-loader"></div>
              </button>
              <button class="dot-btn">
                <div class="dot-loader">
                  <span></span>
                  <span></span>
                  <span></span>
                  <span></span>
                </div>
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "eggplore-content-one",
};
</script>
<style></style>
