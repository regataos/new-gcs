<template>
  <main class="main-content">
    <section class="slideshow">
      <div class="slideshow-inner">
        <div class="slides">
          <div class="slide is-active">
            <div class="slide-content">
              <div class="caption">
                <div class="title slide-title1"></div>
                <div class="text slide-desc1">
                  <p></p>
                </div>
                <a class="btn" @click="slide_function1()">
                  <span class="btn-inner slide-button1"></span>
                </a>
              </div>
            </div>
            <div class="image-container">
              <img alt="" class="image slide-img1" />
            </div>
          </div>

          <div class="slide">
            <div class="slide-content">
              <div class="caption">
                <div class="title slide-title2"></div>
                <div class="text slide-desc2">
                  <p></p>
                </div>
                <a class="btn" @click="slide_function2()">
                  <span class="btn-inner slide-button2"></span>
                </a>
              </div>
            </div>
            <div class="image-container">
              <img alt="" class="image slide-img2" />
            </div>
          </div>

          <div class="slide">
            <div class="slide-content">
              <div class="caption">
                <div class="title slide-title3"></div>
                <div class="text slide-desc3">
                  <p></p>
                </div>
                <a class="btn" @click="slide_function3()">
                  <span class="btn-inner slide-button3"></span>
                </a>
              </div>
            </div>
            <div class="image-container">
              <img alt="" class="image slide-img3" />
            </div>
          </div>

          <div class="slide">
            <div class="slide-content">
              <div class="caption">
                <div class="title slide-title4"></div>
                <div class="text slide-desc4">
                  <p></p>
                </div>
                <a class="btn" @click="slide_function4()">
                  <span class="btn-inner slide-button4"></span>
                </a>
              </div>
            </div>
            <div class="image-container">
              <img alt="" class="image slide-img4" />
            </div>
          </div>
        </div>

        <div class="pagination">
          <div class="pagination2">
            <div data-index="0" @click="changeSlideDot" class="item is-active">
              <span class="icon">1</span>
            </div>
            <div data-index="1" @click="changeSlideDot" class="item">
              <span class="icon">2</span>
            </div>
            <div data-index="2" @click="changeSlideDot" class="item">
              <span class="icon">3</span>
            </div>
            <div data-index="3" @click="changeSlideDot" class="item">
              <span class="icon">4</span>
            </div>
          </div>
        </div>
        <div class="arrows">
          <div @click="changeSlide" class="arrow prev">
            <span class="svg svg-arrow-left">
              <svg
                enable-background="new 0 0 14 26"
                height="26px"
                id="svg4-Layer_1"
                version="1.1"
                viewBox="0 0 14 26"
                width="14px"
                x="0px"
                xml:space="preserve"
                xmlns="http://www.w3.org/2000/svg"
                xmlns:xlink="http://www.w3.org/1999/xlink"
                y="0px"
              >
                <path
                  d="M13,26c-0.256,0-0.512-0.098-0.707-0.293l-12-12c-0.391-0.391-0.391-1.023,0-1.414l12-12c0.391-0.391,1.023-0.391,1.414,0s0.391,1.023,0,1.414L2.414,13l11.293,11.293c0.391,0.391,0.391,1.023,0,1.414C13.512,25.902,13.256,26,13,26z"
                />
              </svg>
              <span class="alt sr-only" />
            </span>
          </div>
          <div @click="changeSlide" class="arrow next">
            <span class="svg svg-arrow-right">
              <svg
                enable-background="new 0 0 14 26"
                height="26px"
                id="svg5-Layer_1"
                version="1.1"
                viewBox="0 0 14 26"
                width="14px"
                x="0px"
                xml:space="preserve"
                xmlns="http://www.w3.org/2000/svg"
                xmlns:xlink="http://www.w3.org/1999/xlink"
                y="0px"
              >
                <path
                  d="M1,0c0.256,0,0.512,0.098,0.707,0.293l12,12c0.391,0.391,0.391,1.023,0,1.414l-12,12c-0.391,0.391-1.023,0.391-1.414,0s-0.391-1.023,0-1.414L11.586,13L0.293,1.707c-0.391-0.391-0.391-1.023,0-1.414C0.488,0.098,0.744,0,1,0z"
                />
              </svg>
              <span class="alt sr-only" />
            </span>
          </div>
        </div>
      </div>
    </section>
  </main>
</template>

<script>
import img1 from "../assets/slide-img1.jpg";
import img2 from "../assets/slide-img2.jpg";
import img3 from "../assets/slide-img3.jpg";
import img4 from "../assets/slide-img4.jpg";

export default {
  data() {
    return {
      userLanguage: "",
      slides: [
        {
          name: "Grand Theft Auto V",
          image: img1,
          texts: {
            pt_BR: {
              descText:
                "Explore o gigantesco e premiado mundo de Los Santos e Blaine County",
              buttonText: "Jogue agora com Rockstar Launcher",
            },
            pt_PT: {
              descText:
                "Explore o gigantesco e premiado mundo de Los Santos e Blaine County",
              buttonText: "Jogue agora com Rockstar Launcher",
            },
            en_US: {
              descText:
                "Explore the award-winning world of Los Santos and Blaine County",
              buttonText: "Play now with Rockstar Launcher",
            },
          },
        },
        {
          name: "Overwatch",
          image: img2,
          texts: {
            pt_BR: {
              descText: "O mundo precisa de heróis",
              buttonText: "Jogue agora com Battle.net",
            },
            pt_PT: {
              descText: "O mundo precisa de heróis",
              buttonText: "Jogue agora com Battle.net",
            },
            en_US: {
              descText: "The world needs heroes",
              buttonText: "Play now with Battle.net",
            },
          },
        },
        {
          name: "Battlefield V",
          image: img3,
          texts: {
            pt_BR: {
              descText:
                "Prove seu valor enfrentando batalhas da Segunda Guerra Mundial",
              buttonText: "Jogue agora com Origin",
            },
            pt_PT: {
              descText:
                "Prove seu valor enfrentando batalhas da Segunda Guerra Mundial",
              buttonText: "Jogue agora com Origin",
            },
            en_US: {
              descText: "Prove your worth by fighting WWII battles",
              buttonText: "Play now with Origin",
            },
          },
        },
        {
          name: "Control",
          image: img4,
          texts: {
            pt_BR: {
              descText:
                "O mundo agora é sua arma em uma luta épica contra um inimigo assustador",
              buttonText: "Jogue agora com a Epic Games Store",
            },
            pt_PT: {
              descText:
                "O mundo agora é sua arma em uma luta épica contra um inimigo assustador",
              buttonText: "Jogue agora com a Epic Games Store",
            },
            en_US: {
              descText:
                "The world is now your weapon in an epic fight against a terrifying enemy",
              buttonText: "Play now with the Epic Games Store",
            },
          },
        },
      ],
      slideshow: null,
    };
  },
  mounted() {
    var user_language = "pt_BR";

    if (user_language.indexOf("pt_BR") > -1 == "1") {
      this.userLanguage = "pt_BR";
    } else if (user_language.indexOf("pt_PT") > -1 == "1") {
      this.userLanguage = "pt_PT";
    } else {
      this.userLanguage = "en_US";
    }

    this.setSlidesData();

    var slideshowDuration = 4000;
    this.slideshow = $(".main-content .slideshow");
    var slideshow = this.slideshow;
    var that = this;

    $(document).ready(function () {
      $(".slide").addClass("is-loaded");

      $(".slideshow .arrows .arrow").on("click", function () {
        that.slideshowNext(slideshow, $(this).hasClass("prev"));
      });

      $(".slideshow .pagination").on("check", function () {
        var slideshow = $(this).closest(".slideshow");
        var pages = $(this).find(".item");
        var index = slideshow.find(".slides .is-active").index();
        pages.removeClass("is-active");
        pages.eq(index).addClass("is-active");
      });

      /* Lazyloading
$('.slideshow').each(function(){
  var slideshow=$(this);
  var images=slideshow.find('.image').not('.is-loaded');
  images.on('loaded',function(){
    var image=$(this);
    var slide=image.closest('.slide');
    slide.addClass('is-loaded');
  });
*/

      var timeout = setTimeout(function () {
        that.slideshowNext(slideshow, false, true);
      }, slideshowDuration);

      slideshow.data("timeout", timeout);
    });

    if ($(".main-content .slideshow").length > 1) {
      $(window).on("scroll", that.homeSlideshowParallax);
    }
    //]]>
  },
  methods: {
    setSlidesData() {
      const lang = this.userLanguage;

      this.slides.forEach((slide, index) => {
        const slideClass = `.slide-img${index + 1}`;
        document.querySelector(slideClass).src = slide.image;

        const titleClass = `.slide-title${index + 1}`;
        document.querySelector(titleClass).innerText = slide.name;

        const textClass = `.slide-desc${index + 1} p`;
        document.querySelector(textClass).innerText =
          slide.texts[lang].descText;

        const buttonClass = `.slide-button${index + 1}`;
        document.querySelector(buttonClass).innerText =
          slide.texts[lang].buttonText;
      });
    },

    changeSlideDot(e) {
      const index = e.target.getAttribute('data-index');
      this.slideshowSwitch(this.slideshow, index);
    },

    changeSlide() {

    },

    slideshowSwitch(slideshow, index, auto) {
      if (slideshow.data("wait")) return;

      var slides = slideshow.find(".slide");
      var pages = slideshow.find(".pagination");
      var activeSlide = slides.filter(".is-active");
      var activeSlideImage = activeSlide.find(".image-container");
      var newSlide = slides.eq(index);
      var newSlideImage = newSlide.find(".image-container");
      var newSlideContent = newSlide.find(".slide-content");
      var newSlideElements = newSlide.find(".caption > *");
      if (newSlide.is(activeSlide)) return;

      newSlide.addClass("is-new");
      var timeout = slideshow.data("timeout");
      clearTimeout(timeout);
      slideshow.data("wait", true);
      var transition = slideshow.attr("data-transition");
      if (transition == "fade") {
        newSlide.css({
          display: "block",
          zIndex: 2,
        });
        newSlideImage.css({
          opacity: 0,
        });

        TweenMax.to(newSlideImage, 1, {
          alpha: 1,
          onComplete: function () {
            newSlide.addClass("is-active").removeClass("is-new");
            activeSlide.removeClass("is-active");
            newSlide.css({ display: "", zIndex: "" });
            newSlideImage.css({ opacity: "" });
            slideshow.find(".pagination").trigger("check");
            slideshow.data("wait", false);
            if (auto) {
              timeout = setTimeout(function () {
                this.slideshowNext(slideshow, false, true);
              }, slideshowDuration);
              slideshow.data("timeout", timeout);
            }
          },
        });
      } else {
        if (newSlide.index() > activeSlide.index()) {
          var newSlideRight = 0;
          var newSlideLeft = "auto";
          var newSlideImageRight = -slideshow.width() / 8;
          var newSlideImageLeft = "auto";
          var newSlideImageToRight = 0;
          var newSlideImageToLeft = "auto";
          var newSlideContentLeft = "auto";
          var newSlideContentRight = 0;
          var activeSlideImageLeft = -slideshow.width() / 4;
        } else {
          var newSlideRight = "";
          var newSlideLeft = 0;
          var newSlideImageRight = "auto";
          var newSlideImageLeft = -slideshow.width() / 8;
          var newSlideImageToRight = "";
          var newSlideImageToLeft = 0;
          var newSlideContentLeft = 0;
          var newSlideContentRight = "auto";
          var activeSlideImageLeft = slideshow.width() / 4;
        }

        newSlide.css({
          display: "block",
          width: 0,
          right: newSlideRight,
          left: newSlideLeft,
          zIndex: 2,
        });

        newSlideImage.css({
          width: slideshow.width(),
          right: newSlideImageRight,
          left: newSlideImageLeft,
        });

        newSlideContent.css({
          width: slideshow.width(),
          left: newSlideContentLeft,
          right: newSlideContentRight,
        });

        activeSlideImage.css({
          left: 0,
        });

        TweenMax.set(newSlideElements, { y: 20, force3D: true });
        TweenMax.to(activeSlideImage, 1, {
          left: activeSlideImageLeft,
          ease: Power3.easeInOut,
        });

        TweenMax.to(newSlide, 1, {
          width: slideshow.width(),
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
          function () {
            newSlide.addClass("is-active").removeClass("is-new");
            activeSlide.removeClass("is-active");
            newSlide.css({
              display: "",
              width: "",
              left: "",
              zIndex: "",
            });

            newSlideImage.css({
              width: "",
              right: "",
              left: "",
            });

            newSlideContent.css({
              width: "",
              left: "",
            });

            newSlideElements.css({
              opacity: "",
              transform: "",
            });

            activeSlideImage.css({
              left: "",
            });

            slideshow.find(".pagination").trigger("check");
            slideshow.data("wait", false);
            if (auto) {
              timeout = setTimeout(function () {
                this.slideshowNext(slideshow, false, true);
              }, slideshowDuration);
              slideshow.data("timeout", timeout);
            }
          }
        );
      }
    },

    slideshowNext(slideshow, previous, auto) {
      var slides = slideshow.find(".slide");
      var activeSlide = slides.filter(".is-active");
      var newSlide = null;
      if (previous) {
        newSlide = activeSlide.prev(".slide");
        if (newSlide.length === 0) {
          newSlide = slides.last();
        }
      } else {
        newSlide = activeSlide.next(".slide");
        if (newSlide.length == 0) newSlide = slides.filter(".slide").first();
      }

      this.slideshowSwitch(slideshow, newSlide.index(), auto);
    },

    homeSlideshowParallax() {
      var scrollTop = $(window).scrollTop();
      if (scrollTop > windowHeight) return;
      var inner = slideshow.find(".slideshow-inner");
      var newHeight = windowHeight - scrollTop / 2;
      var newTop = scrollTop * 0.8;

      inner.css({
        transform: "translateY(" + newTop + "px)",
        height: newHeight,
      });
    },
  },
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
