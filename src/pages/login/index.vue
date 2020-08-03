<template>
  <view>
    <view class="border"></view>
    <view class="login">
      login
    </view>
  </view>
</template>
<script>
export default{
  components: {
  },
  data() {
    return {
    }
  },
  onShareAppMessage() {
    return {
      title: '你好',
      path: '/pages/login/index'
    }
  }
}
</script>
<style lang="scss" scoped>
.border{
  width: 100%;
  height: 1px;
  position: fixed;
  left: 0;
  top: 0;
  background: rgba(0,0,0,0.1);
}
.login{
  height: 2000rpx;
}
</style>