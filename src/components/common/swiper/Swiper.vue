<template>
  <div id="hy-swiper">
    <div class="swiper">
      <slot></slot>
    </div>

    <slot name="indicator"></slot>

    <div class="indicator">
      <slot name="indicator">
        <div>

        </div>
      </slot>
    </div>
  </div>
</template>

<script>
  export default {
    name: "Swiper",
    props: {
      interval: {   // 图片滚动时间
        type: Number,
        default: 2000
      },
      animDuration: {
        type: Number,
        default: 300
      },
      moveRatio: {
        type: Number,
        default: 0.3
      },
      showIndicator: {
        type: Boolean,
        default: true
      }
    },
    data(){
      return {
        slideCount: 0,
        totalWidth: 0,
        swiperStyle: {},
        currentIndex: 1,
        scrolling: false  // 是否正在滚动
      }
    },
    mounted(){
      // 操作DOM，在前后添加 Slide
      setTimeout(() => {
        this.handleDom()

        // 开启定时器
        this.startTimer()
      }, 100);
    },
    methods: {
      /* 定时器处理函数 */ 
      startTimer: function (){
        this.playTimer = window.setInterval( () => {
          this.currentIndex++
          this.scrollContent(-this.currentIndex * this.totalWidth)
        }, this.interval)
      },
      stopTimer: function (){
        window.clearInterval(this.playTimer);
      },

      /* 使图片滚动到正确的位置 */ 
      scrollContent: function (currentPosition){
        // 设置正在滚动
        this.scrolling = true

        // 开始滚动动画
        this.swiperStyle.transition = 'transform' + this.animDuration + 'ms'
        this.setTransform(currentPosition)

        // 判断滚动到的位置
        this.checkPosition()

        // 滚动完成
        this.scrolling = false
      },

      /* 校验正确的位置 */
      checkPosition: function (){
        window.setTimeout( () => {
          // 校验正确的位置
          this.swiperStyle.transition = '0ms';
          if (this.currentIndex >= this.slideCount +1) {
            this.currentIndex =1
            this.setTransform(-this.currentIndex * this.totalWidth)
          } else if (this.currentIndex <=0) {
            this.currentIndex = ths.slideCount
            this.setTransform(-this.currentIndex * this.totalWidth)
          }

          // 结束移动后的回调
          this.$emit('transitionEnd', this.currentIndex-1)
        }, this.animDuration)
      },

      /* 设置滚动的位置 */
      setTransform: function (position){
        this.swiperStyle.transform = 'translated(${position}px, 0, 0)'
        this.swiperStyle['-webkit-transform'] = 'translated(${position}px), 0, 0'
        this.swiperStyle['-ms-transform'] = 'translated(${position}px, 0, 0)'
      },

      /* 操作DOM，在DOM前后添加 Slide */ 
      handleDom: function (){
        // 获取要操作的元素
        let swiperEl = document.querySelector('.swiper')
        let slidesEls = swiperEl.getElementsByClassName('slide')

        // 保存个数
        this.slideCount = slidesEls.length

        // 如果大于1个，那么在前后分别添加一个slide
        if (this.slideCount > 1) {
          let cloneFirst = slidesEls[0].cloneNode(true)
          let cloneLast = slidesEls[this.slideCount - 1].cloneNode(true)
          swiperEl.insertBefore(cloneFirst, slidesEls[0])
          swiperEl.appendChild(cloneFirst)
          this.totalWidth = swiperEl.offsetWidth
          this.swiperStyle = swiperEl.style
        }

      // 让swiper元素显示第一个（目前显示的是前面添加的最后一个元素）
      this.setTransform(-this.totalWidth)
      },

      /* 拖动事件的处理 */ 
      touchStart: function (e){
        // 如果正在滚动，不可以拖动
        if (this.scrolling) return;

        // 停止定时器
        this.stopTimer()

        // 保存开始滚动的位置
        this.startX = e.touches[0].pageX
      },

      touchMove: function (e) {
        // 巨酸出用户拖动的距离
        this.currentX = e.touches[0].pageX
        this.distance = this.currentX - this.startX
        let currentPosition = -this.currentIndex * this.totalWidth
        let moveDistance = this.distance + currentPosition

        // 设置当前的位置
        this.setTransform(moveDistance)
      },

      
    }
}
</script>

<style>

</style>