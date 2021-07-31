<template>
  <div>
    <nav-bar>
      <template #center>center</template>
    </nav-bar>
  </div>
</template>

<script>
  import NavBar from 'components/common/tabbar/NavBar';
  import {getHomeMultidata} from 'network/home';

  export default {
    name: "Home",
    components: {
      NavBar
    },
    data(){
      return {
        banners: [],
        recommend: []
      }
    },
    created(){
      // 请求多个数据
      getHomeMultidata().then( res => {
        console.log(res)
        // 将网络请求返回的数据保存起来，否则函数执行完之后变量res会被销毁
        // 当“网络请求返回的数据”的引用计数为0时，这个数据会被当作垃圾回收
        this.banners = res.data.banners
        this.recommend = res.data.recommend
      })
    }
  }
</script>

<style scoped>

</style>