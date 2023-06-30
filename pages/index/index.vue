<template>
	<view>
		<view class="index-top">

		</view>
		<view class="index-bottom" :style="'height:' + bottom_height + 'px;'">
			<scroll-view scroll-y="true">
				<!-- 轮播图 -->
				<view class="swiper-container">
					<swiper class="swiper-info" circular autoplay="true" interval="5000" duration="500">
						<swiper-item v-for="(item,index) in swiper_items" :key="index"
							:style="'background-image: url(' + item.img_url + ');'">
						</swiper-item>
					</swiper>
				</view>
				<!--头像-->
				<view class="avatar-content">
					<view class="avatar-place"></view>
					<image class="avatar" mode="aspectFit" src="@/static/logo.jpg" @error="imageError"></image>
				</view>
				<!--描述-->
				<view class="school-desc">
					<text>综合性虚拟大学</text>
					<text>双一流建设高校</text>
					<text>996/007</text>
				</view>
				<!-- 菜单九宫格 -->
				<view class="school-menu">
					<view v-for="(item,index) in school_menu" :key="index" class="menu-item"
						@click="navigatePage(item.page)">
						<view class="menu-icon" :style="'background-color:' + item.color + ';'">
							<text :class="'iconfont ' + item.iconfont"></text>
						</view>
						<text>{{ item.info }}</text>
					</view>
				</view>
				<!-- 信息展示卡片列表 -->
				<view class="school-card">
					<view class="card-item" v-for="(item,index) in school_card" :key="index" :style="'background-image: url('+item.url+')'">
						<view class="card-info">
							<text><text :class="'iconfont '+item.icon"></text>{{item.info}}</text>
						</view>
					</view>
				</view>
				<!--  -->
				<view>
					<u-subsection :list="list" :current="current" mode="button" activeColor="#de443a"
						inactiveColor="#888888" @change="sectionChange"></u-subsection>
					<view>
						<view class="news-card">
							<view class="news-item">
								<image mode="aspectFit" src="http://www.whut.edu.cn/xywh/lgfw/202204/W020220408619634056357.jpg" @error="imageError"></image>
								<view class="news-info">
									<text class="news-desc">2023年山河大学2023年山河大学</text>
									<text>2023-06-29<text class="iconfont icon-jifen"
											style="margin-left: 20upx;">519</text></text>
								</view>
							</view>
							<view class="news-item">
								<image mode="aspectFit" src="http://www.whut.edu.cn/xywh/lgfw/202204/W020220408619648902538.jpg" @error="imageError"></image>
								<view class="news-info">
									<text class="news-desc">2023年山河大学简章</text>
									<text>2023-06-29<text class="iconfont icon-jifen"
											style="margin-left: 20upx;">519</text></text>
								</view>
							</view>
						</view>
					</view>
				</view>

			</scroll-view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				bottom_height: '0',
				swiper_items: [
					{
						img_url: "https://img1.baidu.com/it/u=2156938474,1038063959&fm=253&fmt=auto&app=138&f=JPEG?w=1500&h=500"
					},
					{
						img_url: "https://img1.baidu.com/it/u=1770479264,4201494596&fm=253&fmt=auto&app=138&f=JPEG?w=640&h=358"
					},
					{
						img_url: "https://img2.baidu.com/it/u=62954069,123298212&fm=253&fmt=auto&app=138&f=JPEG?w=780&h=320"
					}
				],
				school_menu: [
					{
						color: '#6d56fe',
						iconfont: 'icon-zhihuixiaoyuan',
						info: '学校概况',
						page: "/pages/school/school"
					},
					{
						color: '#f49d48',
						iconfont: 'icon-jihua',
						info: '招生计划'
					},
					{
						color: '#735dfe',
						iconfont: 'icon-shu-duidie',
						info: '专业信息'
					},
					{
						color: '#61db9b',
						iconfont: 'icon-dasaizhangcheng',
						info: '招生章程'
					},
					{
						color: '#a836f2',
						iconfont: 'icon-shipin',
						info: '校园视频'
					},
					{
						color: '#5cc8b9',
						iconfont: 'icon-fengcai',
						info: '校园风采'
					},
					{
						color: '#fd6f75',
						iconfont: 'icon-shuben',
						info: '历年分数'
					},
					{
						color: '#7998f2',
						iconfont: 'icon-shouye',
						info: '在线咨询'
					}
				],
				school_card: [
					{
						url:"https://www.nyist.edu.cn/__local/C/46/F6/37408E46F6BB2CD05F8B99623F3_F5AEA777_22A5B.jpg",
						icon:"icon-shipin",
						info:"遇见山河"
					},
					{
						url:"https://www.nyist.edu.cn/__local/D/60/CA/5ACDED287FF7CE18853171F6781_F665CBC5_240E0.jpg",
						icon:"icon-fengcai",
						info:"学长学姐带你上大学"
					},
					{
						url:"https://www.nyist.edu.cn/__local/5/3A/FD/29C9D8E6A86020AA2358AEC6BFD_D7000A16_FAC75.jpg",
						icon:"icon-fengjing",
						info:"山河风光"
					},
					{
						url:"https://www.nyist.edu.cn/__local/6/F3/49/221DF09D3DBCAB171CCADA6CB3D_05DB16E4_38CF8.jpg",
						icon:"icon-xiaoli",
						info:"学年校历"
					}
				],
				list: ['招生快讯', '通知公告'],
				current: 1
			}
		},
		onLoad() {
			uni.getSystemInfo({
				success: (res) => {
					// this.bottom_height = res.windowHeight - uni.upx2px(60)
					this.bottom_height = res.windowHeight
					// console.log(res.windowHeight)
				}
			})


		},
		methods: {
			sectionChange(index) {
				this.current = index;
			},
			navigatePage(page) {
				if (page == null) {
					return
				}
				uni.navigateTo({
					url: page
				})
			}
		}
	}
</script>

<style scoped>
	.index-bottom {
		/* background-color: gray; */
	}

	scroll-view {
		height: 100%;
		/* background-color: gray; */
	}

	.swiper-container {
		width: 95%;
		border-radius: 5%;
		margin: 10upx auto;
		/* 阴影 */
		box-shadow: 5upx 10upx 10upx #ccc;
	}

	.swiper-info {
		border-radius: 5%;
	}

	swiper-item {
		/* 背景图片铺满 */
		border-radius: 5%;
		background-size: 100% 100%;
		background-image: url("https://img2.baidu.com/it/u=4056604448,2622182953&fm=253&fmt=auto&app=138&f=JPEG?w=840&h=394");
	}

	.avatar-content {
		width: 100%;
		height: 100upx;
		display: flex;
	}

	.avatar {
		width: 200upx;
		height: 200upx;
		margin: 0 auto;
		border-radius: 50%;
		position: relative;
		top: -100upx;
	}

	.school-desc {
		width: 100%;
		display: grid;
		text-align: center;
		grid-template-columns: auto auto auto;
		justify-content: space-evenly;
		align-items: center;
		align-content: center;
		justify-items: stretch;
		margin: 30upx 0;
	}

	.school-desc text {
		font-size: 30upx;
		background-color: #00afb9;
		color: #fff;
		font-weight: bold;
		/* 左右边框圆形上下不变 */
		border-radius: 30upx;
		padding: 10upx 15upx;
	}

	.school-menu {
		display: grid;
		grid-template-columns: 1fr 1fr 1fr 1fr;
	}


	.menu-item {
		margin: 20upx 0upx;
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	.menu-icon {
		width: 80upx;
		height: 80upx;
		display: flex;
		justify-content: center;
		align-items: center;
		background-color: #6d56fe;
		border-radius: 40%;
		color: #fff;
		margin-bottom: 20upx;
	}

	.menu-icon .iconfont {
		font-size: 50upx;
	}

	.school-card {
		width: 98%;
		margin: 20upx auto;
		display: grid;
		grid-template-columns: 1fr 1fr;
		/* 格子间距 */
		grid-gap: 10upx;
	}

	.card-item {
		position: relative;
		height: 250upx;
		border-radius: 5%;
		background-size: 100% 100%;
		background-image: url("https://www.nyist.edu.cn/__local/C/46/F6/37408E46F6BB2CD05F8B99623F3_F5AEA777_22A5B.jpg");
	}

	.card-info {
		width: 200upx;
		height: 90upx;
		/* 定位到右下角 */
		position: absolute;
		bottom: 7%;
		right: 0;
		display: flex;
		flex-direction: row;
		justify-content: space-evenly;
		align-items: center;
		color: #fff;
		font-weight: bold;
		font-size: 98%;
		padding-right: 10upx;
		background-image: linear-gradient(to right, rgba(28, 145, 223, 0), rgba(28, 145, 223, 1));

	}

	.card-info .iconfont {
		margin-right: 10upx;
	}

	.news-item {
		width: 98%;
		height: 220upx;
		margin: 5upx auto;
		display: grid;
		grid-template-columns: 30% 70%;
		align-items: center;
		border-bottom: #ccc solid 1upx;
	}

	.news-item image {
		width: 100%;
		height: 200upx;
		border-radius: 10%;
	}

	.news-info {
		height: 200upx;
		display: flex;
		flex-direction: column;
		justify-content: space-around;
		align-items: flex-start;
		margin-left: 20upx;
	}

	.news-desc {
		/* 文字最多三行，超出省略号 */
		display: -webkit-box;
		-webkit-box-orient: vertical;
		-webkit-line-clamp: 3;
		overflow: hidden;
	}
</style>