<template>
    <tab-bar>
      <tab-bar-item path='/home' activeColor='orange'>
        <template #item-icon>
          <img src="~assets/img/tabbar/home01.png" alt="">
        </template>
        
        <template #item-icon-active>
          <img src="~assets/img/tabbar/home01_active.png" alt="">
        </template>
        
        <template #item-text>
          <div>首页</div>
        </template>
        
      </tab-bar-item>
      <tab-bar-item path='/category'>
        <template #item-icon>
          <img src="~assets/img/tabbar/category01.png" alt="">
        </template>
        
        <template #item-icon-active>
          <img src="~assets/img/tabbar/category01_active.png" alt="">
        </template>
        
        <template #item-text>
          <div>分类</div>
        </template>
        
      </tab-bar-item>
      <tab-bar-item path='/shopcart'>
        <template #item-icon>
          <img src="~assets/img/tabbar/shopcart01.png" alt="">
        </template>
        
        <template #item-icon-active>
          <img src="~assets/img/tabbar/shopcart01_active.png" alt="">
        </template>
        
        <template #item-text>
          <div>购物车</div>
        </template>
        
      </tab-bar-item>
      <tab-bar-item path='/profile'>
        <template #item-icon>
          <img src="~assets/img/tabbar/profile01.png" alt="">
        </template>
        
        <template #item-icon-active>
          <img src="~assets/img/tabbar/profile01_active.png" alt="">
        </template>
        
        <template #item-text>
          <div>我的</div>
        </template>
        
      </tab-bar-item>
    </tab-bar>
</template>

<script>
import TabBar from 'components/common/tabbar/TabBar.vue'
import TabBarItem from 'components/common//tabbar/TabBarItem.vue'

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