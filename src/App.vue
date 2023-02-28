<template>
  <div id="app">
    <div class="app__circle">
      <div
        class="app__gray-sector"
        @mouseover="isGray = true"
        @mouseleave="isGray = false"
      >
        <img src="./assets/images/gray.svg" alt="сектор." />
      </div>
      <div
        class="app__pink-sector"
        @mouseover="isPink = true"
        @mouseleave="isPink = false"
      >
        <img src="./assets/images/pink.svg" alt="сектор." />
      </div>
      <div
        class="app__green-sector"
        @mouseover="isGreen = true"
        @mouseleave="isGreen = false"
      >
        <img src="./assets/images/green.svg" alt="сектор." />
      </div>
    </div>

    <ul class="app__legend">
      <li
        class="app__legend-item"
        :class="{ 'app__legend-item_active': isPink }"
      >
        <div class="app__color app__color_pink" />
        <p class="app__legend-text">Розовый сегмент</p>
      </li>
      <li
        class="app__legend-item"
        :class="{ 'app__legend-item_active': isGreen }"
      >
        <div class="app__color app__color_green" />
        <p class="app__legend-text">Зеленый сегмент</p>
      </li>
      <li
        class="app__legend-item"
        :class="{ 'app__legend-item_active': isGray }"
      >
        <div class="app__color app__color_gray" />
        <p class="app__legend-text">Серый сегмент</p>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "App",
  data: function () {
    return {
      isPink: false,
      isGreen: false,
      isGray: false,
    };
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "GHEA Grapalat";
}

@font-face {
  font-family: "GHEA Grapalat";
  font-style: normal;
  font-weight: 400;
  font-display: swap;
  src: url("./assets/fonts/GHEAGrpalatReg.otf") format("opentype");
}

#app {
  width: 100%;
  height: 100vh;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
}

.app__circle {
  width: 515px;
  height: 515px;
  margin: auto 100px auto 0;
  position: relative;
  clip-path: circle(50% at 50% 50%);
}

.app__gray-sector {
  position: absolute;
  top: 0;
  right: 0;
}

.app__gray-sector::after {
  content: "";
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  right: 0;
  background-color: rgba(0, 0, 0, 0);
  transition: all 0.3s linear;
}

.app__gray-sector:hover::after {
  background-color: rgba(0, 0, 0, 0.2);
}

.app__pink-sector {
  position: absolute;
  top: 0;
  right: 0;
  transition: all 0.3s linear;
}

.app__pink-sector::after {
  content: "";
  width: 100%;
  height: 257px;
  position: absolute;
  top: 0;
  right: 0;
  background-color: rgba(0, 0, 0, 0);
  transition: all 0.3s linear;
}

.app__pink-sector:hover::after {
  background-color: rgba(0, 0, 0, 0.2);
}

.app__green-sector {
  position: absolute;
  bottom: 1px;
  left: 1px;
  clip-path: polygon(0% 0%, 57% 0, 100% 48%, 77% 100%, 0 100%);
}

.app__green-sector::after {
  content: "";
  width: 100%;
  height: 100%;
  position: absolute;
  bottom: 0;
  left: 0;
  background-color: rgba(0, 0, 0, 0);
  transition: all 0.3s linear;
}

.app__green-sector:hover::after {
  background-color: rgba(0, 0, 0, 0.2);
}

.app__green-sector:hover .app__legend-item_green {
  opacity: 1;
  border-bottom: 1px solid #97bb31;
}

.app__legend-item {
  display: flex;
  flex-direction: row;
  align-items: center;
  margin-bottom: 20px;
  opacity: 0.6;
  transition: all 0.3s ease-in-out;
}

.app__legend-item:last-of-type {
  margin-bottom: 0;
}

.app__legend-item_active {
  opacity: 1;
  transition: all 0.3s ease-in-out;
}

.app__legend-text {
  font-style: normal;
  font-weight: 400;
  font-size: 16px;
  line-height: 1;
  letter-spacing: 0.05em;
  text-transform: uppercase;
}

.app__color {
  width: 14px;
  height: 14px;
  margin-right: 13px;
}

.app__color_pink {
  background-color: #ff69b4;
}

.app__color_green {
  background-color: #97bb31;
}

.app__color_gray {
  background-color: #d9d9d9;
}
</style>
