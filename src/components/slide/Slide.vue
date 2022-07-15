<template>
  <div :class="`slide ${isActive ? 'is-active' : ''}`">
    <div class="slide-content">
      <div class="caption">
        <div class="title">{{ name }}</div>
        <div class="text">{{ desc }}</div>
        <a class="btn" @click="btnClick(btnAction)">
          <span class="btn-inner">
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
        case "openRockstar":
          this.openLauncher("rockstar");
          break;

        case "openBattleNet":
          this.openLauncher("battlenet");
          break;

        case "openOrigin":
          this.openLauncher("origin");
          break;

        case "openEpicGames":
          this.openLauncher("epicgames");
          break;

        default:
          this.openLauncher("steam");
      }
    },
    openLauncher(launcher) {
      alert("Abrindo " + launcher);
    },
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
  height: 450px;
  z-index: 1;
  transition: opacity 0.3s ease;

  &.is-active {
    display: block;
  }

  .slide-content {
    height: 100%;
    font-family: "Roboto", sans-serif;
    font-weight: 500;
    text-align: center;
    display: flex;
    align-items: end;

    .caption {
      padding-bottom: 46px;
      width: 1000px;
      margin-left: 245px;
      z-index: 1;

      .title {
        font: 300 50px/1.2 "Oxygen", sans-serif;
        letter-spacing: 0.2em;
        text-transform: uppercase;
        font-weight: 700;
        text-shadow: 5px 1px 10px rgba(0, 0, 0, 0.8);
      }

      .text {
        margin-bottom: 12px;
        font-size: 20px;
        text-shadow: 1px 2px 5px rgba(0, 0, 0, 0.8);
      }

      .btn {
        font: 14px/1.2 "Oxygen", sans-serif;
        cursor: pointer;
        position: relative;
        display: inline-block;
        padding: 15px 20px;
        background-color: rgb(4 4 4 / 32%);
        border: 1px solid #e1e1e1;
        border-radius: 2em;
        letter-spacing: 0.2em;
        text-transform: uppercase;
        transition: color 0.1s linear 0.05s;
        overflow: hidden;
        box-shadow: 0px 2px 4px -1px rgb(0 0 0 / 20%),
          0px 4px 5px 0px rgb(0 0 0 / 14%), 0px 1px 10px 0px rgb(0 0 0 / 12%);

        -webkit-backdrop-filter: blur(10px);
        backdrop-filter: blur(10px);

        &::before {
          content: "";
          position: absolute;
          left: 0;
          width: 100%;
          background: #e1e1e1;

          top: 50%;
          height: 1px;
          opacity: 0;
          transition: height 0.2s ease, top 0.2s ease, opacity 0s linear 0.2s;
        }

        &:hover {
          color: #373737;

          &::before {
            top: 0;
            height: 100%;
            opacity: 1;
            transition: height 0.2s ease, top 0.2s ease, opacity 0s linear 0s;
          }
        }

        .btn-inner {
          font-weight: 600;
          position: relative;
        }
      }
    }
  }

  .image-container {
    position: absolute;
    top: 0;
    height: 150%;

    &::before {
      content: "";
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.5);
    }
    .image {
      width: 100%;
      background-position: center;
      background-size: 100%;
      background-repeat: no-repeat;
      object-fit: cover;
      height: 100%;
    }
  }
}
</style>
