<template>
  <div id="app">
    <side-bar></side-bar>
    <div class="main">
      <router-view></router-view>
    </div>
  </div>
</template>

<script>
import SideBar from './components/SideBar/SideBar.vue'

export default {
  name: 'app',
  components: {
    SideBar
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  text-align: center;
}

.main {
  float: left;
  height: 100%;
  width: 95%;
  background-color: #eff2f7;
  overflow: auto;
}
</style>
