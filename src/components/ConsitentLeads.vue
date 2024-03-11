<template>
  <div class="section">
    <div class="columns">
      <div class="text-wrapper">
        <h2 class="header-text"></h2>
        <p class="text">
          We combine disruptive marketing techniques with proven tech solutions
          to provide maximum business value.
        </p>
      </div>
      <div class="column-wrapper">
        <div
          v-for="(item, index) in columnHeights"
          :key="index"
          class="column"
          :style="{ height: `${item[0]}px` }"
        >
          <div class="label">{{ item[1] }}</div>
        </div>
      </div>
      <div class="chart-container">
        <div
          v-for="(row, index) in row"
          :key="index"
          class="row"
          :style="{ marginLeft: row.margin }"
        >
          <div class="row-contant">
            <p class="row-text">{{ row.text }}</p>
            <p class="row-number">{{ row.number }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);

export default {
  data() {
    return {
      columnHeights: [
        [171, 25],
        [266, 40],
        [341, 50],
        [305, 45],
        [194, 30],
        [266, 40],
        [341, 50],
        [423, 65],
        [305, 45],
        [407, 60],
        [509, 75],
        [597, 88],
        [445, 65],
        [682, 100],
      ],
      row: [
        { margin: "0px", number: 1150, text: "Revenue generated for clients" },
        {
          margin: "765px",
          number: 1200,
          text: "Conversationd opened",
        },
        { margin: "0px", number: 378, text: "Leads generated via targeted" },
        {
          margin: "1057px",
          number: 197,
          text: "Calls scheduled for clients",
        },
      ],
    };
  },
  methods: {
    animateText() {
      gsap.to(".header-text", {
        scrollTrigger: {
          trigger: ".header-text",
          start: "start 85%",
        },
        text: "Consitent leads flow to streamline </br>Your business growth.",
        duration: 3,
      });

      gsap.set(".text", { opacity: 0 });

      gsap.to(".text", {
        scrollTrigger: {
          trigger: ".text",
          start: "-100px 95%",
        },
        opacity: 1,
        duration: 3,
      });
    },

    animateBars() {
      this.columnHeights.forEach((item, index) => {
        gsap.set(`.column:nth-child(${index + 1})`, { height: 100 });

        gsap.to(`.column:nth-child(${index + 1})`, {
          scrollTrigger: {
            trigger: ".column-wrapper",
            start: "-100px center",
            end: "bottom bottom",
            scrub: true,
          },
          height: item[0],
        });

        gsap.to(`.column:nth-child(${index + 1}) .label`, {
          scrollTrigger: {
            trigger: ".column-wrapper",
            start: "-100px center",
            end: "bottom bottom",
            scrub: true,
          },
          opacity: 1,
        });
      });
    },

    animateColumns() {
      gsap.to(".row", {
        width: "100%",
        opacity: 1,
        duration: 1,
        scrollTrigger: {
          trigger: ".chart-container",
          start: "top 80%",
          end: "top 30%",
          scrub: true,
        },
      });
    },
  },
  mounted() {
    this.animateText();
    this.animateBars();
    this.animateColumns();
  },
};
</script>

<style scoped>
.columns {
  position: relative;
}

.column-wrapper {
  display: flex;
  overflow-x: auto;
  align-items: end;
  position: absolute;
  top: 256px;
  height: 710px;
  width: 100%;
  padding: 0 20px 10px;
}

.column {
  width: 133px;
  height: 100px;
  background: #e63e3a;
  margin-right: 1px;
  position: relative;
}

.label {
  position: absolute;
  top: -20px;
  left: 50%;
  transform: translateX(-50%);
  color: #e63e3a;
  font-size: 15px;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
  opacity: 0;
}

.text-wrapper {
  display: block;
  padding: 107px 20px 0;
}

.header-text {
  display: block;
  height: 158px;
  margin-bottom: 58px;
  color: var(--dark-text, #101820);
  font-size: 82px;
  font-style: normal;
  font-weight: 400;
  line-height: 96%;
}

.text {
  color: #101820;
  font-size: 22px;
  font-style: normal;
  font-weight: 400;
  line-height: 120.5%;
}

.chart-container {
  margin-top: 610px;
  display: flex;
  flex-direction: column;
  gap: 10px;
  height: 100vh;
  overflow-x: hidden;
}

.row {
  height: 100px;
  background-color: #101820;
  width: 0%;
  opacity: 0;
  box-sizing: border-box;
  display: flex;
  align-content: center;
}

.row-contant {
  display: flex;
  align-items: center;
}

.row-text,
.row-number {
  color: #e63e3a;
}

.row-text {
  max-width: 200px;
  margin-right: 21px;
  text-align: right;
  font-size: 22px;
  font-style: normal;
  font-weight: 400;
  line-height: 120.5%;
}

.row-number {
  font-size: 52px;
}

.row:first-of-type {
  justify-content: end;
}

.row:first-of-type .row-contant {
  margin-right: 42px;
}
.row:last-of-type .row-contant {
  margin-left: 42px;
}
.row:first-of-type .row-contant {
  margin-right: 42px;
}
</style>
