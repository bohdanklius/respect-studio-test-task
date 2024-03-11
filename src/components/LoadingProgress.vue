<template>
  <div class="section">
    <div class="text-wrapper" v-if="showText">
      <h2 class="text-container"></h2>
      <h2 class="text-container2"></h2>
    </div>

    <div class="progress-container" v-if="loading">
      <div class="overlay"></div>
      <div class="progress-bar" v-if="!showText">
        <h1 class="progress-bar">{{ progressValue }}</h1>
      </div>
    </div>
  </div>
</template>

<script>
import { gsap } from "gsap";
import { TextPlugin } from "gsap/TextPlugin";

gsap.registerPlugin(TextPlugin);

export default {
  data() {
    return {
      loading: true,
      progressValue: "02",
      showText: false,
    };
  },
  methods: {
    async animateText() {
      await this.delay(500);

      gsap.to(".text-container", {
        duration: 1,
        text: "Respect",
      });

      gsap.to(".text-container2", {
        duration: 1,
        text: ".Studio",
      });

      await this.delay(1000);

      gsap.to(".progress-container", { y: -1600, duration: 2 });
    },

    updateProgress() {
      const presetValues = [
        "06",
        "12",
        "24",
        "48",
        "56",
        "64",
        "76",
        "82",
        "98",
        "100",
      ];
      let currentIndex = 0;

      const interval = setInterval(() => {
        this.progressValue = presetValues[currentIndex];

        if (currentIndex === presetValues.length - 1) {
          clearInterval(interval);
          this.showText = true;
          this.animateText();
        } else {
          currentIndex++;
        }
      }, 200);
    },

    delay(ms) {
      return new Promise((resolve) => setTimeout(resolve, ms));
    },
  },
  mounted() {
    this.updateProgress();
  },
};
</script>

<style scoped>
.text-wrapper {
  z-index: 2;
  position: absolute;
  top: 20px;
  left: 20px;
}

.text-container,
.text-container2 {
  font-size: 56px;
  color: #e63e3a;
  font-weight: bold;
}

.text-container2 {
  writing-mode: vertical-lr;
}

.progress-container {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1;
}

.overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: #1e1e1e;
}

.progress-bar {
  position: absolute;
  bottom: 0;
  right: 0;
  color: #e63e3a;
  text-align: right;
  text-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
  -webkit-text-stroke-width: 1;
  -webkit-text-stroke-color: #000;
  font-size: 230px;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
  z-index: 1;
}
</style>
