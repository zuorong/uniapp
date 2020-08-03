<template>
  <view class="about-wrap">
    <Navbar title="关于我们" border />
    <view class="scroll">
      <scroll-view class="scroll-view_H" scroll-y="true">
        <view class="item" v-for="item in 10" :key="item">
          about{{item}}
          <button @tap="onTap">tap</button>
        </view>
      </scroll-view>
    </view>
  </view>
</template>
<script>
import Navbar from '@/components/Navbar'
export default{
  components: {
    Navbar
  },
  data() {
    return {
    }
  },
  methods: {
    onTap() {
      console.log(getApp().globalData)
      console.log(getCurrentPages())
    }
  },
  onShareAppMessage() {
    return {
      title: '关于我们',
      path: '/pages/about/index'
    }
  }
}
</script>
<style lang="scss" scoped>
.about-wrap{
}
</style>