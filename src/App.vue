<template>
  <TopBar v-model="pageAtual" />
  <SideBar />

  <Home v-if="pageAtual == 'home'"/>
  <AllGames v-if="pageAtual == 'allgames'"/>
  <Settings v-if="pageAtual == 'settings'"/>

  {{ pageAtual }}
</template>

<script>
import TopBar from "./components/TopBar.vue";
import SideBar from "./components/SideBar.vue";

import Home from "./pages/Home.vue";
import AllGames from "./pages/AllGames.vue";
import Settings from "./pages/Settings.vue";

import { defineComponent, ref } from "vue";

export default defineComponent({
  setup() {
    const pageAtual = ref('home');
    return {
      pageAtual,
    };
  },
  components: {
    TopBar,
    SideBar,
    Home,
    AllGames,
    Settings
  },
});
</script>

<style>
body {
  font-family: Oxygen;
  font-weight: 300;
  color: #fff;
  padding: 0;
  margin: 0;
  -webkit-touch-callout: none;
  -webkit-user-select: none;
  user-select: none;
  background-color: #2a2e33;
  background-repeat: no-repeat;
}

@font-face {
  font-family: "Oxygen";
  src: url("src/fonts/Oxygen.otf") format("truetype");
}
</style>
