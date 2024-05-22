<template>
	<view>
		<view class="user-card">
			<image class="user-avatar" mode="aspectFit" :src="userInfo.avatar" @error="imageError"></image>
			<view>
				<view v-if="isLogin" class="user-info">
					<view class="user-name">{{ userInfo.username }}</view>
					<view class="user-level">{{ userInfo.userNumber }}</view>
				</view>
				<view v-if="!isLogin" class="user-login" @click="login()">
					<view>登录/注册</view>
				</view>
			</view>
		</view>
		<view class="user-menu">
			<view class="menu-item" v-for="(item, index) in userMenu" :key="index">
				<view>
					<text :class="'iconfont ' + item.iconfont"></text>
					<text>{{ item.info }}</text>
				</view>
				<view>
					<text class="iconfont icon-bangzhujinru"></text>
				</view>
			</view>
		</view>
		<text class="ridicule">登录api天天变，获取用户信息api天天出问题，你们官方的开发团队怎么搞的</text>
		<button v-if="isLogin" class="login-out" @click="loginOut">退出登录</button>

		<u-popup :show="show" @close="close" :closeOnClickOverlay="show" :closeable="true">
			<view class="popup-notice">
				设置头像和昵称
			</view>
			<view class="get-avatar">
				<view class="avatar-notice">获取头像</view>
				<button open-type="chooseAvatar" @chooseavatar='onChooseAvatar' >
				<image :src="userInfo.avatar" mode=""></image>
				</button>
			</view>
			<view class="get-name">
				<view class="name-notice">设置昵称</view>
				<input type="nickname" v-model="userInfo.username" placeholder="请输入昵称">
			</view>
			<button class="mini-btn" type="primary" @click="submitInfo" >提交</button>
		</u-popup>
	</view>
</template>

<script>
export default {
	data() {
		return {
			isLogin: false,
			show: false,
			userInfo: {
				username: '微信用户',
				userNumber: '00000001',
				avatar: '../../static/avatar.jpg'
			},
			userMenu: [
				{
					iconfont: 'icon-shouji',
					info: '绑定手机',
					page: 'bindPhone',
					color: '#f5a623'
				},
				{
					iconfont: 'icon-fankui',
					info: '意见反馈',
					page: 'feedback',
					color: '#f5a623'
				},
				{
					iconfont: 'icon-wode1',
					info: '关于我们',
					page: 'aboutUs',
					color: '#f5a623'
				}
			]
		}
	},
	methods: {
		login() {
			uni.login({
				provider: 'weixin',
				success: function (loginRes) {
					// console.log(loginRes)
				}
			});
			this.isLogin = true
			this.show = true
		},
		loginOut(){
			this.isLogin = false
			this.userInfo = {
				username: '微信用户',
				userNumber: '00000001',
				avatar: '../../static/avatar.jpg'
			}
			//退出登录操作
		},
		close() {
			this.show = false
		},
		onChooseAvatar(e) {
			console.log(e.detail)
			this.userInfo.avatar = e.detail.avatarUrl
			this.userInfo.username = e.detail.value
		},
		submitInfo(){
			this.show = false;
			//todo 提交信息到服务器
			console.log(this.userInfo)
		}
	}
}
</script>

<style scoped>
.user-card {
	display: flex;
	flex-direction: row;
	justify-content: flex-start;
	align-items: center;
	background-color: #d6e4ef;
	width: 95%;
	height: 350upx;
	margin: 0 auto;
	border-radius: 30upx;
}

.user-avatar {
	width: 150upx;
	height: 150upx;
	border-radius: 50%;
	margin: 30upx 30upx 30upx 50upx;
}

.user-login {
	display: flex;
	flex-direction: row;
	justify-content: center;
	align-items: center;
}

.user-login :first-child {
	/* 下划线 */
	border-bottom: #0f1215 1upx solid;
}

.user-name {
	font-size: large;
	height: 50upx;
	margin-bottom: 30upx;
}

.user-menu {
	width: 95%;
	margin: 0 auto;
	margin-top: 40upx;
	border-top: #d6e4ef 1upx solid;
	border-bottom: #d6e4ef 1upx solid;
}

.menu-item {
	display: flex;
	flex-direction: row;
	justify-content: space-between;
	align-items: center;
	width: 95%;
	margin: 0 auto;
	height: 100upx;
	border-bottom: #d6e4ef 1upx solid;
}

/* css选择器过滤最后一个子元素 */
.menu-item:last-child {
	border-bottom: none;
}

.menu-item .iconfont {
	margin-right: 20upx;
}

.popup-notice{
	width:100%;
	height: 80upx;
	/* 文字垂直水平居中 */
	display: flex;
	flex-direction: row;
	justify-content: center;
	align-items: center;
	margin-top: 30upx;
}
.get-avatar{
	margin-top: 60upx;
}
.get-name{
	margin-bottom:0;
}
.get-avatar,.get-name{
	width: 100%;
	height: 150upx;
	display: flex;
    flex-direction: row;
    justify-content: flex-start;
    align-items: center;
	margin-left: 50upx;
}
.get-avatar button{
	width: 100upx;
	height: 100upx;
	background-color: rgb(255, 255, 255,0);
	border-radius: 50%;
	padding: 0;
	margin: 0;
}
.get-avatar button,.get-name input{
	margin-left: 50upx;
}
.get-avatar button image{
	width: 100%;
	height: 100%;
}

.mini-btn{
	margin-bottom: 60upx;
	width: 250upx;
}

.login-out{
	width: 300upx;
	position: absolute;
	bottom: 30upx;
	background-color: #fff;
	left: 50%;
	transform: translateX(-50%);
}


.ridicule{
	width:80%;
	margin: 100upx auto;
	color: red;
	font-size: smaller;
	/* 文字自动换行 */
	word-wrap: break-word;
	/* 文字垂直水平居中 */
	display: flex;
	flex-direction: row;
	justify-content: center;
	align-items: center;

}
</style>