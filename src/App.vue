<script setup>
import TopBar from './components/TopBar.vue'
import SideBar from './components/SideBar.vue'
import Home from './pages/Home.vue'
</script>

<template>
  <TopBar />
  <SideBar />
  <Home />
</template>

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

@font-face{
  font-family: "Oxygen";
  src: url('src/fonts/Oxygen.otf') format('truetype');
}
</style>
