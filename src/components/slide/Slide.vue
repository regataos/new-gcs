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
      <img alt="" class="image slide-img1" :src="image"/>
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
      console.log('btnClick XD')
    }
  },
});
</script>

<style></style>
