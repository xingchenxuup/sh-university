<script>
export default {
	onLaunch: function () {
		//如果是微信小程序
		//#ifdef MP-WEIXIN
		// console.log(wx.getLaunchOptionsSync())
		let scene = wx.getLaunchOptionsSync().scene
		//1154 微信朋友圈分享
		if (scene != 1154) {
			uni.showShareMenu({
				withShareTicket: true,
				menus: ['shareAppMessage', 'shareTimeline']
			})
		}
		//#endif


	},
	onShow: function () {

	},
	onHide: function () {

	}

}
</script>

<style lang="scss">
/*每个页面公共css */
@import "@/static/iconfont/iconfont.css";
@import "@/static/typeface/ali_typeface.css";
@import "uview-ui/index.scss";
@import "@/static/iconfont/iconfont-weapp-icon.css"

// * {
// 	font-family: "iconfont" !important;
// }
</style>