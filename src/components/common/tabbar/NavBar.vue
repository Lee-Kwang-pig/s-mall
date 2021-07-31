<template>
  <div class="nav-bar">
    <div class="left"><slot name="left"></slot></div>
    <div class="center"><slot name="center"></slot></div>
    <div class="right"><slot name="right"></slot></div>
  </div>
</template>

<script>
  export default {
    name: 'NavBar',
  }
</script>

<style>
  .nav-bar {
    display: flex;
    background-color: #bf0;
  }

  .left, .right {
    width: 60px;
    background-color: sandybrown;
  }

  .center {
    flex: 1;
  }

  .left, .right, .center {
    height: 44px;
    line-height: 44px;
    text-align: center;
    font-size: 22px;
  }
</style>