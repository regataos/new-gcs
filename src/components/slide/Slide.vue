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
    btnAction: String,
  },
  methods: {
    btnClick(action) {
      switch(action) {
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

<style></style>
