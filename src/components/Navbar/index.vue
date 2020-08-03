<template>
  <view class="navbar_wrap" :style="{paddingBottom: (statusHeight + menuHeight) + 'px'}">
  <!-- <view class="navbar_wrap"> -->
    <view :style="{background: background}" :class="{navbar: true, border: border ? true : false}">
      <!-- 状态栏 -->
      <view class="navbar_status_bar" :style="{height: statusHeight + 'px'}"></view>
      <!-- 状态栏 -->

      <!-- 标题栏 -->
      <view :style="{height: menuHeight + 'px'}" class="navbar_title">
        <view
          v-if="pages.count !== 1 || (!pages.route.includes('pages/index/index'))" class="navbar_back"
          @tap="onBack"
        />
        <text>{{ title }}</text>
      </view>
      <!-- 标题栏 -->
    </view>

    <!-- <slot></slot> -->
  </view>
</template>
<script>
const app = getApp()
const globalData = app.globalData
export default{
  props: {
    title: {
      type: String,
      default() {
        return ''
      }
    },
    border: {
      type: Boolean,
      default() {
        return false
      }
    },
    background: {
      type: String,
      default() {
        return '#fff'
      }
    }
  },
  data() {
    return {
      menuHeight: globalData.menuHeight + globalData.menuBotton * 2,
      statusHeight: globalData.statusHeight,
      pages: {
        count: 0,
        route: ''
      }
    }
  },
  mounted() {
    const pages = getCurrentPages()
    const len = pages.length
    this.pages.count = len
    if (len === 1) {
      this.pages.route = pages[0].route
    } else {
      this.pages.route = ''
    }
  },
  methods: {
    onBack() {
      uni.navigateBack()
    }
  }
}
</script>
<style lang="scss" scoped>
.navbar_wrap{
}
.navbar{
  width: 100%;
  position: fixed;
  left: 0;
  top: 0;
  z-index: 1000;
  &.border{
    border-bottom: 1px solid rgba(0,0,0,0.1);
  }
  .navbar_status_bar {
    width: 100%;
  }
  .navbar_title{
    width: 100%;
    color: #000;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 16px;
    font-weight: bold;
    position: relative;
  }
  .navbar_back{
    width: 50px;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    position: absolute;
    left: 0;
    top: 0;
    &:after{
      width: 10px;
      height: 10px;
      border-color: #000;
      border-width: 2px;
      border-style: solid;
      border-top: none;
      border-right: none;
      transform: rotate(45deg);
      display: block;
      content: "";
    }
  }
}
</style>