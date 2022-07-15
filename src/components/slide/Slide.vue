<template>
  <div :class="`slide ${isActive ? 'is-active' : ''} is-loaded`">
    <div class="slide-content">
      <div class="caption">
        <div class="title slide-title1">{{ name }}</div>
        <div class="text slide-desc1">
          <p>{{ desc }}</p>
        </div>
        <a class="btn" @click="btnClick()">
          <span class="btn-inner slide-button1">
            {{ btnText }}
          </span>
        </a>
      </div>
    </div>
    <div class="image-container">
      <img alt="" class="image slide-img1" :src="image" />
    </div>
  </div>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  props: {
    isActive: Boolean,
    image: String,
    name: String,
    desc: String,
    btnText: String,
  },
  setup(props) {
    function btnClick() {
      console.log("btnClick XD");
    }
  },
});
</script>

<style lang="scss" scoped>
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
}
</style>
