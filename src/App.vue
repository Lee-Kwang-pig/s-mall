<template>
  <div id="app">
    <main-tab-bar></main-tab-bar>
    <router-view/>
  </div>
</template>

<script>
  import MainTabBar from 'components/content/MainTabBar.vue'

  export default {
    name: 'App',
    components: {
      MainTabBar,
    }
  }
</script>

<style>
  @import 'assets/css/basscss.css';
</style>
