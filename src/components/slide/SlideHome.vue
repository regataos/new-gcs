<template>
  <main class="main-content">
    <section class="slideshow">
      <div class="slideshow-inner">
        <div class="slides">
          <Slide
            v-for="(slide, index) in slides"
            :isActive="index == 0"
            :image="slide.image"
            :name="slide.name"
            :desc="slide.texts[userLanguage].descText"
            :btnText="slide.texts[userLanguage].buttonText"
          />

          <div class="pagination">
            <div class="pagination2">
              <div
                v-for="(slide, index) in slides"
                :class="`item ${index == 0 ? 'is-active' : ''}`"
                @click="changeSlide(index)"
              >
                <span class="icon">{{ index + 1 }}</span>
              </div>
            </div>
          </div>

          <div class="arrows">
            <Arrow :direction="'prev'" @arrowClick="arrowClick" />
            <Arrow :direction="'next'" @arrowClick="arrowClick" />
          </div>
        </div>
      </div>
    </section>
  </main>
</template>

<script>
import Slide from "./Slide.vue";
import Arrow from "./Arrow.vue";
import { nextTick } from "vue";

export default {
  data() {
    return {
      userLanguage: "pt_BR",
      slides: [],
      slideshowDuration: 1000,
    };
  },
  async beforeCreate() {
    const jsonLink =
      "https://raw.githubusercontent.com/regataos/jsons_e_images/main/jsons/gameAccessHomeSlides.json";
    this.slides = await fetch(jsonLink).then((slideData) => slideData.json());

    await nextTick(() => {
      this.setTimeoutChangeSlide();
    });
  },
  methods: {
    changeSlide(newIndex, auto) {
      const slideshow = $('.slideshow');
      const newSlideshow = document.querySelector('.slideshow');
      const slideshowWidth = newSlideshow.offsetWidth;

      if (newSlideshow.getAttribute("data-wait") == 'true') return

      var slides = slideshow.find(".slide");
      var activeSlide = document.querySelector('.slide.is-active');
      var activeSlideIndex = Array.from(slides).indexOf(activeSlide);
      var activeSlideImage = activeSlide.querySelector(".image-container");

      var newSlide = slides.eq(newIndex);

      slides = newSlideshow.querySelectorAll(".slide");      
      var testeNewSlide = slides[newIndex];
      var newSlideImage = testeNewSlide.querySelector(".image-container");
      var newSlideContent = testeNewSlide.querySelector(".slide-content");
      var newSlideElements = testeNewSlide.querySelectorAll(".caption > *");

      if (testeNewSlide == activeSlide) return;
      newSlide.addClass("is-new");
      
      newSlideshow.setAttribute("data-wait", true);

      const newSlideRight = newIndex > activeSlideIndex ? 0 : "";
      const newSlideLeft = newIndex > activeSlideIndex ? "auto" : 0;
      const newSlideImageRight = newIndex > activeSlideIndex ? -slideshowWidth / 8 : "auto";
      const newSlideImageLeft = newIndex > activeSlideIndex ? "auto" : -slideshowWidth / 8;
      const newSlideImageToRight = newIndex > activeSlideIndex ? 0 : "";
      const newSlideImageToLeft = newIndex > activeSlideIndex ? "auto" : 0;
      const newSlideContentLeft = newIndex > activeSlideIndex ? "auto" : 0;
      const newSlideContentRight = newIndex > activeSlideIndex ? 0 : "auto";
      const activeSlideImageLeft = newIndex > activeSlideIndex ? -slideshowWidth / 4 : slideshowWidth / 4;

      newSlide.css({
        display: "block",
        width: 0,
        right: newSlideRight,
        left: newSlideLeft,
        zIndex: 2,
      });

      newSlideImage.width = slideshowWidth;
      newSlideImage.right = newSlideImageRight;
      newSlideImage.left = newSlideImageLeft;

      newSlideContent.style.width = slideshowWidth;
      newSlideContent.style.left = newSlideContentLeft;
      newSlideContent.style.right = newSlideContentRight;

      activeSlideImage.style.left = 0;

      TweenMax.set(newSlideElements, { y: 20, force3D: true });
      TweenMax.to(activeSlideImage, 1, {
        left: activeSlideImageLeft,
        ease: Power3.easeInOut,
      });
      TweenMax.to(newSlide, 1, {
        width: slideshowWidth,
        ease: Power3.easeInOut,
      });
      TweenMax.to(newSlideImage, 1, {
        right: newSlideImageToRight,
        left: newSlideImageToLeft,
        ease: Power3.easeInOut,
      });

      TweenMax.staggerFromTo(
        newSlideElements,
        0.8,
        { alpha: 0, y: 60 },
        { alpha: 1, y: 0, ease: Power3.easeOut, force3D: true, delay: 0.6 },
        0.1,
        () => {
          testeNewSlide.classList.add("is-active")
          testeNewSlide.classList.remove("is-new");
          activeSlide.classList.remove("is-active");

          newSlide.css({
            display: "",
            width: "",
            left: "",
            zIndex: "",
          });

          newSlideImage.width = "";
          newSlideImage.right = "";
          newSlideImage.left = "";

          newSlideContent.style.width = "";
          newSlideContent.style.left = "";

          newSlideElements.forEach(element => {
            element.style.opacity = "";
            element.style.transform = "";
          })

          activeSlideImage.style.left = "";
    
          var actualPage = newSlideshow.querySelector(".item.is-active");
          var pages = newSlideshow.querySelectorAll(".item");
          var newIndex = Array.from(newSlideshow.querySelectorAll(".slide")).findIndex(slide => slide.classList.contains('is-active'))
          actualPage.classList.remove("is-active");
          pages[newIndex].classList.add("is-active");

          newSlideshow.setAttribute("data-wait", false);
          if (auto) this.setTimeoutChangeSlide();
        }
      );
    },

    setTimeoutChangeSlide() {
      setTimeout(() => {
        this.arrowClick("next", true);
      }, this.slideshowDuration);
    },

    arrowClick(direction, auto) {
      const slides = Array.from(document.querySelectorAll(".slide"));
      const indexSlideActive = slides.findIndex((slide) =>
        slide.classList.contains("is-active")
      );
      let indexNewSlide;

      if (direction == "prev") indexNewSlide = indexSlideActive - 1;
      else indexNewSlide = indexSlideActive + 1;

      if (indexNewSlide < 0) indexNewSlide = slides.length - 1;
      if (indexNewSlide > slides.length - 1) indexNewSlide = 0;

      this.changeSlide(indexNewSlide, auto);
    },
  },
  components: { Slide, Arrow },
};
</script>

<style lang="scss">
.btn {
  display: inline-block;
  padding: 15px 20px 13px 20px;
  color: #fff;
  font-weight: 800;
  text-decoration: none;
  position: relative;
  background-color: rgb(4 4 4 / 32%);
  -webkit-backdrop-filter: blur(10px);
  backdrop-filter: blur(10px);
  border: 1px solid #e1e1e1;
  border-radius: 2em;
  font: 14px/1.2 "Oxygen", sans-serif;
  letter-spacing: 0.2em;
  text-align: center;
  text-indent: 2px;
  text-transform: uppercase;
  transition: color 0.1s linear 0.05s;
  cursor: pointer;
  box-shadow: 0px 2px 4px -1px rgb(0 0 0 / 20%),
    0px 4px 5px 0px rgb(0 0 0 / 14%), 0px 1px 10px 0px rgb(0 0 0 / 12%);

  &::before {
    content: "";
    display: block;
    position: absolute;
    top: 50%;
    left: 0;
    width: 100%;
    height: 1px;
    background: #e1e1e1;
    border-radius: 2em;
    z-index: 1;
    opacity: 0;
    transition: height 0.2s ease, top 0.2s ease, opacity 0s linear 0.2s;
  }
  &::after {
    transition: border 0.1s linear 0.05s;
  }
  &:hover {
    color: #373737;
    transition: color 0.1s linear 0s;

    &::before {
      top: 0;
      height: 100%;
      opacity: 1;
      transition: height 0.2s ease, top 0.2s ease, opacity 0s linear 0s;
    }
    &::after {
      border-color: #373737;
      transition: border 0.1s linear 0s;
    }
  }
  .btn-inner {
    font-weight: 600;
    position: relative;
    z-index: 2;
  }
}

.slideshow {
  overflow: hidden;
  position: relative;
  width: 100%;
  height: 470px;
  z-index: 1;

  .slideshow-inner {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
  }

  .slides {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 450px;
    z-index: 1;
  }

  .slide {
    display: none;
    overflow: hidden;
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 1;
    opacity: 0;
    transition: opacity 0.3s ease;

    &.is-active {
      display: block;
    }

    &.is-loaded {
      opacity: 1;
    }

    .caption {
      margin-top: 250px;
      padding: 0 100px;
      width: 1000px;
      margin-left: 245px;
    }

    .image-container {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      object-fit: cover;
      height: 650px;
      background-position: 50% 30%;
      background-position: center;
      z-index: 1;
      background-size: cover;

      &::before {
        content: "";
        display: block;
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, 0.5);
      }
    }

    .image {
      width: 101%;
      background-position: 50% 30%;
      background-size: 100%;
      background-repeat: no-repeat;
      object-fit: cover;
      height: 100%;
    }

    .title {
      margin: 0 auto 5px;
      max-width: 1000px;
      font: 300 50px/1.2 "Oxygen", sans-serif;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      font-weight: 700;
      text-shadow: 5px 1px 10px rgba(0, 0, 0, 0.8);
    }

    .slideshow .slide .text {
      margin: 0 auto;
      max-width: 1000px;
      font-size: 20px;
      line-height: 1.4;
    }

    .text p {
      margin: 0;
      text-shadow: 1px 2px 5px rgba(0, 0, 0, 0.8);
    }

    .btn {
      margin: 15px 0 0;
      border-color: #707070;
      margin-left: 0px;

      &::before {
        background: #fff;
      }
    }
  }

  .slide-content {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 2;
    color: #fff;
    font-family: "Roboto", sans-serif;
    font-weight: 500;
    text-align: center;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .pagination {
    position: absolute;
    bottom: 35px;
    width: 100%;
    right: 0;
    height: 12px;
    cursor: default;
    z-index: 2;
    text-align: center;

    .item {
      display: inline-block;
      padding: 15px 5px;
      position: relative;
      width: 36px;
      height: 32px;
      cursor: pointer;
      text-indent: -999em;
      margin-top: 25px;
      margin-left: 5px;
      margin-right: 5px;
      z-index: 1;

      &::before {
        content: "";
        display: block;
        position: absolute;
        top: 15px;
        left: 5px;
        width: 36px;
        height: 4px;
        background: rgba(255, 255, 255, 0.5);
        transition: background 0.2s ease;
      }

      &::after {
        width: 0;
        background: #fff;
        z-index: 2;
        transition: width 0.2s ease;
      }

      & + .page {
        margin-left: -2px;
      }

      &:hover::before,
      &.is-active::before {
        background-color: #fff;
      }
    }
  }

  .arrows {
    .arrow {
      margin: -33px 0 0;
      padding: 20px;
      position: absolute;
      top: 50%;
      cursor: pointer;
      z-index: 3;
    }

    .prev {
      left: 275px;

      &:hover .svg {
        left: -10px;
      }
    }

    .next {
      right: 30px;

      &:hover .svg {
        left: 10px;
      }
    }
  }

  .svg {
    position: relative;
    left: 0;
    width: 14px;
    height: 26px;
    fill: #fff;
    transition: left 0.2s ease;
  }

  .pagination2 {
    position: relative;
    margin-left: 245px;
  }
}
</style>
