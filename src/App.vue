<script>
	export default {
		onLaunch: function() {
      console.log('App Launch')
      this.setNavBarInfo()
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
    },
    globalData: {
      //全局数据管理
      navBarHeight: 0, // 导航栏高度
      menuBotton: 0, // 胶囊距底部间距（保持底部间距一致）
      menuRight: 0, // 胶囊距右方间距（方保持左、右间距一致）
      menuHeight: 0, // 胶囊高度（自定义内容可与胶囊高度保证一致）
      statusHeight: 0, // 状态栏高度
      fontSizeSetting: 16 // 用户字体大小
    },
    methods: {
      setNavBarInfo () {
        // 获取系统信息
        const systemInfo = uni.getSystemInfoSync()
        // 胶囊按钮位置信息
        const menuButtonInfo = uni.getMenuButtonBoundingClientRect()
        // 导航栏高度 = 状态栏到胶囊的间距（胶囊距上距离-状态栏高度） * 2 + 胶囊高度 + 状态栏高度
        this.globalData.navBarHeight = (menuButtonInfo.top - systemInfo.statusBarHeight) * 2 + menuButtonInfo.height + systemInfo.statusBarHeight
        this.globalData.menuBotton = menuButtonInfo.top - systemInfo.statusBarHeight
        this.globalData.menuRight = systemInfo.screenWidth - menuButtonInfo.right
        this.globalData.menuHeight = menuButtonInfo.height
        this.globalData.statusHeight = systemInfo.statusBarHeight
        this.globalData.fontSizeSetting = systemInfo.fontSizeSetting
      }
    }
	}
</script>

<style lang="scss">
  @import "uview-ui/index.scss";
	/*每个页面公共css */
</style>
