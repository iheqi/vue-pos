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
}

.main {
  height: 100%;
}
</style>
