<template>
	<view>
		<text style="color: red;font-weight: bold;">没有美术细胞，没有想法，大家有没有好看的页面推荐一下</text>
		<!-- 用户信息卡片 -->
		<view class="login-card">
			<view class="login-info">
				<view class="avatar-content">
					<image class="avatar" mode="aspectFit" src="@/static/avatar.jpg" @error="imageError"></image>
				</view>
				<view v-if="!isLogin" class="login-tip">
					<text>登录 <text style="font-weight: normal;">&nbsp;/&nbsp;</text> 注册</text>
				</view>
				<view v-if="isLogin" class="user-name">
					<text>用户名</text>
				</view>
			</view>
			<view class="user-info">
				<view class="user-info-item">
					<text>0</text>
					<text>xxx</text>
				</view>
				<view class="user-info-item">
					<text>0</text>
					<text>xxx</text>
				</view>
				<view class="user-info-item">
					<text>0</text>
					<text>xxx</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				isLogin: false
			}
		},
		methods: {
			
		}
	}
</script>

<style scoped>
/* 登陆卡片相关css */
.login-card {
	width: 95%;
	height: 350upx;
	/* 金色背景 */
	background-color: #fcdebc;
	background-image: url("@/static/xingkong.png");
	border-radius: 20upx;
	margin: 0 auto;
	box-shadow: 0 0 20upx #ccc;
}

.login-info {
	width: 100%;
	height: 100px;
	margin-left: 30upx;
	display: flex;
	flex-direction: row;
	justify-content: flex-start;
	align-items: center
}

/* 头像相关css */
.avatar-content {
	justify-content: center;
}

.avatar {
	width: 150upx;
	height: 150upx;
	border-radius: 50%;
	border: 5upx solid #fff;
}

/* 登陆注册入口css */
.login-tip {
	/* 黑色字体加粗 */
	color: #000;
	font-weight: bold;
	font-size: large;
	margin-left: 20upx;
}

/* 用户个人信息概况css */
.user-info {
	width: 100%;
	height: 150upx;
	display: flex;
	flex-direction: row;
	justify-content: space-between;
	align-items: center
}

.user-info-item {
	width: 33.3%;
	height: 100%;
	display: flex;
	flex-direction: column;
	justify-content: center;
	align-items: center;
}

.user-info-item text:nth-child(1) {
	font-size: 35upx;
	/* font-weight: bold; */
	color: #525035;
	margin-bottom: 10upx;
}

.user-info-item text:nth-child(2) {
	font-size: 28upx;
	/* font-weight: bold; */
	color: #c0a169;
}
</style>