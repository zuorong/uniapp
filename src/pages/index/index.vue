<template>
  <view class="container">
    <Navbar background="none" title="学习中心" />
    <view class="wrap">
      <view class="header">
        <image class="bg" src="@/static/bg.png" />
      </view>
      <view class="home-tab">
        <view v-for="(item, index) in list" :key="index" :class="{active: item.active}" @tap="onTap(item)">
          <text>{{ item.name }}</text>
        </view>
      </view>
      
      <view class="scroll">
        <scroll-view class="scroll-view_H" scroll-y="true" @scroll="onScroll">
          <view v-for="item in 20" :key="item" class="scroll-item">
            C{{item}}
            <navigator url="/pages/login/index" hover-class="navigator-hover">
              <button type="default">lgin</button>
            </navigator>
            <navigator url="/pages/about/index" hover-class="navigator-hover">
              <button type="default">about</button>
            </navigator>
          </view>
        </scroll-view>
      </view>
    </view>
  </view>
</template>

<script>
import Navbar from '@/components/Navbar'
	export default {
    components: {
      Navbar
    },
		data() {
			return {
        list: [
          {
            name: '我的班级',
            active: true
          },
          {
            name: '考试',
            active: false
          }
        ]
			}
    },
    onShareAppMessage() {
      return {
        title: '你好',
        path: '/pages/login/index'
      }
    },
    onShow() {
      console.log('show')
    },
		methods: {
      onTap(item) {
        console.log(getCurrentPages())
        this.list.forEach(n => n.active = false)
        item.active = true
        console.log(item)
      },
      onScroll() {
      }
		}
	}
</script>

<style lang="scss">
.wrap{
  width: 100%;
  height: 100vh;
  display: flex;
  flex-direction: column;
  position: absolute;
  left: 0;
  top: 0;
  .header{
    width: 100%;
    height: 408rpx;
    .bg{
      width: 100%;
      height: 100%;
    }
  }
  .home-tab{
    display: flex;
    height: 92rpx;
    border-bottom: 1px solid #E5E5E5;
    border-radius: 16rpx 16rpx 0px 0px;
    background: #fff;
    position: relative;
    margin: 0 28rpx;
    margin-top: -16rpx;
    view{
      flex: 1;
      display: flex;
      justify-content: center;
      align-items: center;
      position: relative;
      &.active:after{
        width: 60rpx;
        height: 6rpx;
        display: block;
        content: "";
        position: absolute;
        left: 50%;
        bottom: 0;
        margin-left: -30rpx;
        background: #0A51C4;
        border-radius: 3rpx;
      }
      &.active{
        text{
          color: #0A51C4;
        }
      }
      text{
        font-size: 32rpx;
        color: #666;
      }
    }
  }
  .scroll{
    flex: 1;
    display: flex;
    flex-direction: column;
    scroll-view{
      max-height: 100%;
      flex: 1;
    }
    .scroll-item{
      height: 300rpx;
      display: flex;
      justify-content: center;
      align-items: center;
      background: silver;
      margin-bottom: 10px;
    }
  }
}
</style>
