<template>
	<view class="info">
		<!-- 轮播图 -->
		<view class="swiper-container">
			<swiper class="swiper-info" autoplay="true" interval="5000" duration="500">
				<swiper-item v-for="(item,index) in swiper_items" :key="index"
					:style="'background-image: url(' + item.img_url + ');'">
				</swiper-item>
			</swiper>
		</view>
		<view class="school-level">
			<text>高校层次</text>
			<view class="level-info">
				<text>虚拟大学</text>
				<text>普通本科</text>
				<text>谨防诈骗</text>
			</view>
		</view>
		<!-- 学校简介的卡片 -->
		<view class="school-card">
			<view class="card-item" v-for="(item,index) in school_info" :key="index">
				<view>
					<text :class="'t-icon '+item.icon"></text>
					<text>{{item.info}}</text>
				</view>
				<view>
					<text>{{item.num}}</text>
					<text>{{item.unit}}</text>
				</view>
			</view>
		</view>
		<!-- 详细介绍 -->
		<rich-text :nodes="content"></rich-text>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				swiper_items: [{
						img_url: "https://img1.baidu.com/it/u=2156938474,1038063959&fm=253&fmt=auto&app=138&f=JPEG?w=1500&h=500"
					},
					{
						img_url: "https://img1.baidu.com/it/u=1770479264,4201494596&fm=253&fmt=auto&app=138&f=JPEG?w=640&h=358"
					},
					{
						img_url: "https://img2.baidu.com/it/u=62954069,123298212&fm=253&fmt=auto&app=138&f=JPEG?w=780&h=320"
					}
				],
				school_info:[
					{
						icon:"t-icon-zhongbiao",
						info:"建校时间",
						num:"2023",
						unit:"年",
					},
					{
						icon:"t-icon-zongzhandimianji",
						info:"占地面积",
						num:"9000",
						unit:"亩",
					},
					{
						icon:"t-icon-xuekeceping",
						info:"国家重点学科",
						num:"0",
						unit:"个",
					},
					{
						icon:"t-icon-keyan",
						info:"科研项目",
						num:"0",
						unit:"个",
					},
					{
						icon:"t-icon-boshi",
						info:"博士点",
						num:"0",
						unit:"个",
					},
					{
						icon:"t-icon-shuoshi",
						info:"硕士点",
						num:"0",
						unit:"个",
					}
				],
				content:`
<p>欢迎来到山河大学，这是一所由山东、山西、河南和河北四省高中毕业生联合创办的虚拟大学。我们致力于为学生提供高质量的教育和全面发展的机会。山河大学融合了四省的文化精髓，创造了独特的学术氛围和校园环境。</p>

<h3>学术优势</h3>

<p>作为一所综合性大学，山河大学提供丰富多样的学术领域和专业课程。我们的教职员工是一支经验丰富、富有激情的团队，他们在各自领域拥有卓越的学术造诣。学生们将有机会接受来自不同省份的优秀教育资源，拓宽自己的学术视野。</p>

<h3>创新科研</h3>

<p>山河大学以创新科研为基石，鼓励学生积极参与科学探索和实践。我们提供先进的实验室设施和研究资源，为学生提供丰富的研究机会。无论是理论研究还是应用探索，学生们将在山河大学找到一个推动他们科研梦想实现的平台。</p>

<h3>全面发展</h3>

<p>山河大学注重学生的全面发展，提供丰富多样的课外活动和社团组织。学生们可以参加学术性的学术团队、社会实践团队、艺术团队等，培养领导能力和团队合作精神。我们还鼓励学生积极参与体育运动和文化活动，促进身心健康的发展。</p>

<h3>虚拟校园</h3>

<p>山河大学拥有先进的虚拟校园平台，为学生提供便捷的学习和交流环境。学生们可以通过在线课程和学习资源进行学习，与教师和同学进行讨论和互动。虚拟校园不仅扩大了学习的空间和时间，还提供了更多国际化的交流机会。</p>

<h3>国际合作</h3>

<p>山河

大学积极推进国际交流与合作，与世界各地的高校建立了广泛的合作关系。我们鼓励学生参加交换项目和国际学术会议，拓展国际视野和跨文化交流能力。</p>
`,
			}
		},
		methods: {

		}
	}
</script>

<style scoped>
	p {
	  text-indent: 2em;
	}
	h3{
		width: 100%;
		text-align: center;
	}
	.info {
		width: 95%;
		margin: 0 auto;
	}

	.swiper-container {
		width: 100%;
		border-radius: 5%;
		margin: 10upx auto;
		/* 阴影 */
		box-shadow: 5upx 10upx 10upx #ccc;
	}

	swiper-item {
		border-radius: 5%;
		background-size: 100% 100%;
	}

	.school-level {
		display: flex;
		flex-direction: row;
		justify-content: flex-start;
		align-items: center;
		margin-top: 40upx;
	}

	.level-info {
		display: flex;
		flex-direction: row;
		justify-content: flex-start;
		align-items: center;
		margin: 0 0 0 40upx;
	}

	.level-info text {
		border: #0084ff solid 2upx;
		margin: 0 10upx;
		padding: 5upx 10upx;
		color: #0084ff;
		font-weight: 520;
	}

	.school-card {
		display: grid;
		grid-template-columns: 50% 50%;
		justify-content: space-around;
		align-items: center;
		justify-items: start;
		grid-gap: 20upx;
		margin: 30upx 0;
	}

	.card-item {
		width: 100%;
		display: flex;
		flex-direction: column;
		justify-content: space-around;
		align-items: flex-start;
		background-color: #f8f8f8;
		border-radius: 10%;
	}

	.card-item view:nth-child(1) {
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
		margin: 20upx 0 10upx 20upx;
	}

	.card-item view:nth-child(1) text:nth-child(1) {
		font-size: 60upx;
	}

	.card-item view:nth-child(1) text:last-child {
		color: #777777;
		margin-left: 20upx;
	}
	
	.card-item view:last-child {
		margin: 10upx 0 10upx 20upx;
	}
	
	.card-item view:last-child text:nth-child(1) {
		font-weight: bold;
	}
	
	.card-item view:last-child text:last-child {
		color: #777777;
		margin-left: 20upx;
	}
</style>