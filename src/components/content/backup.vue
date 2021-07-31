// 备份
<template>
    <tab-bar>
      <tab-bar-item path='/home' activeColor='orange'>
        <img slot="item-icon" src="../../assets/img/tabbar/home01.png" alt="">
        <img slot="item-icon-active" src="../../assets/img/tabbar/home01_active.png" alt="">
        <div slot="item-text">首页</div>
      </tab-bar-item>
      <tab-bar-item path='/category'>
        <img slot="item-icon" src="../../assets/img/tabbar/category01.png" alt="">
        <img slot="item-icon-active" src="../../assets/img/tabbar/category01_active.png" alt="">
        <div slot="item-text">分类</div>
      </tab-bar-item>
      <tab-bar-item path='/shopcart'>
        <img slot="item-icon" src="../../assets/img/tabbar/shopcart01.png" alt="">
        <img slot="item-icon-active" src="../../assets/img/tabbar/shopcart01_active.png" alt="">
        <div slot="item-text">购物车</div>
      </tab-bar-item>
      <tab-bar-item path='/profile'>
        <img slot="item-icon" src="../../assets/img/tabbar/profile01.png" alt="">
        <img slot="item-icon-active" src="../../assets/img/tabbar/profile01_active.png" alt="">
        <div slot="item-text">我的</div>
      </tab-bar-item>
    </tab-bar>
</template>

<script>
import TabBar from '../common/tabbar/TabBar.vue'
import TabBarItem from '../common/tabbar/TabBarItem.vue'

  export default {
    name: "MainTabBar",
    components: {
        TabBar,
        TabBarItem
    },
    data () {
      return {}
    },
    methods:{}
  }
</script>

<style scoped>

</style>