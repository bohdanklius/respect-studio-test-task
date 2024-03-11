<template>
  <div class="section section_header1">
    <div>
      <h3 class="background_header">Digital Marketing <br />Agency</h3>
      <div class="background-container">
        <img :src="currentImage" :key="currentImage" class="background-image" />
      </div>
    </div>
  </div>

  <div class="section section_header">
    <div class="">
      <div class="header">
        <div class="links_wrapper">
          <a href="/">
            <img src="../assets/Logo.svg" alt="Logo" />
          </a>
          <ul class="link_list">
            <li class="list"><a class="link" href="/">Services</a></li>
            <li class="list"><a class="link" href="/">Case Studies</a></li>
            <li class="list"><a class="link" href="/">Blog</a></li>
            <li class="list"><a class="link" href="/">About us</a></li>
          </ul>
          <ul class="link_list">
            <li class="list"><a class="link" href="/">We're hiring</a></li>
            <li class="list"><a class="link" href="/">Contacts</a></li>
          </ul>
          <div class="">
            <button class="header_button">
              <span class="button_arrow">
                <img src="../assets/Arrow_right.svg" alt="Arrow right" />
              </span>
              Book a call
            </button>
          </div>
        </div>
      </div>
      <div class="text_wrapper">
        <h2 class="header_text"></h2>
      </div>
      <div class="text-container-wrapper">
        <p class="text-content">
          B2B Marketing & LinkedIn Lead <br />Generation agency
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import { gsap } from "gsap";
import { TextPlugin } from "gsap/TextPlugin";
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger, TextPlugin);

export default {
  data() {
    return {
      images: [
        require("../assets/images/header_image1.webp"),
        require("../assets/images/header_image2.webp"),
        require("../assets/images/header_image3.webp"),
        require("../assets/images/header_image4.webp"),
      ],
      currentImageIndex: 0,
      intervalId: null,
    };
  },
  computed: {
    currentImage() {
      return this.images[this.currentImageIndex];
    },
  },
  methods: {
    changeBackground() {
      this.currentImageIndex =
        (this.currentImageIndex + 1) % this.images.length;
    },

    animateText() {
      gsap.to(".header_text", {
        scrollTrigger: {
          trigger: ".header_text",
          start: "start 85%",
        },
        text: "Growing <br />businesses by <br />building <br />relationships",
        duration: 3,
      });

      gsap.set(".text-content", { opacity: 0 });

      gsap.to(".text-content", {
        scrollTrigger: {
          trigger: ".text-content",
          start: "-100px 95%",
        },
        opacity: 1,
        duration: 3,
      });
    },
  },
  mounted() {
    this.intervalId = setInterval(() => {
      this.changeBackground();
    }, 1000);
    this.animateText();
  },
  beforeUnmount() {
    clearInterval(this.intervalId);
  },
};
</script>

<style scoped>
.background-container {
  max-width: 1920px;
  height: 869px;
}

.background-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.background_header {
  color: #e63e3a;
  position: absolute;
  top: 21px;
  right: 20px;
  text-align: end;
  text-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
  font-size: 18px;
  font-style: normal;
  font-weight: 400;
  line-height: 120%;
}

.section {
  background-color: #e63e3a;
}

.links_wrapper {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 19px 20px;
}

.link_list {
  display: flex;
  list-style: none;
}

.link {
  color: #101820;
  font-size: 22px;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
  text-decoration: none;
  margin-right: 80px;
}

.header_button {
  color: #e63e3a;
  font-size: 22px;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
  padding: 13px 18px;
  background: #101820;
  cursor: pointer;
}

.button_arrow {
  margin-right: 67px;
  margin-left: 96px;
}

.text_wrapper {
  padding: 74px 20px 190px;
}

.header_text {
  color: #101820;
  text-align: right;
  font-size: 135px;
  font-style: normal;
  font-weight: 400;
  line-height: 96%;
  letter-spacing: -4.05px;
  display: block;
  height: 520px;
}

.text-container-wrapper {
  padding: 0 0 30px 20px;
}

.text-content {
  color: #101820;
  font-size: 22px;
  font-style: normal;
  font-weight: 400;
  line-height: 120.5%;
}
</style>
