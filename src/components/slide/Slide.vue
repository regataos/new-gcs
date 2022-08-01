<template>
  <div :class="`slide ${isActive ? 'is-active' : ''} is-loaded`">
    <div class="slide-content">
      <div class="caption">
        <div class="title slide-title1">{{ name }}</div>
        <div class="text slide-desc1">
          <p>{{ desc }}</p>
        </div>
        <a class="btn" @click="btnClick(btnAction)">
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
    btnAction: String,
  },
  methods: {
    btnClick(action) {
      switch (action) {
        case 'openRockstar':
          this.openLauncher('rockstar');
          break;

        case 'openBattleNet':
          this.openLauncher('battlenet');
          break;

        case 'openOrigin':
          this.openLauncher('origin');
          break;

        case 'openEpicGames':
          this.openLauncher('epicgames');
          break;

        default:
          this.openLauncher('steam');
      }
    },
    openLauncher(launcher) {
      alert('Abrindo ' + launcher)
    }
  }
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

    .btn {
       margin: 15px 0 0;
    border-color: #707070;
    margin-left: 0px;
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

  }
}
</style>
