<template>
  <div class="tab-bar">
    <slot></slot>
  </div>
</template>

<script>
  export default {
    name: "TabBar",
    data () {
      return {}
    },
    methods:{}
  }
</script>

<style scoped>
    .tab-bar {
        display: flex;
        background-color: #f0ebe5;
        height: 49px;
        align-content: center;
        justify-content: center;

        position: fixed;
        bottom: 0;
        left: 0;
        right: 0;
    }
</style>