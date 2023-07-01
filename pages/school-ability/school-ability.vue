<template>

	<view class="ability-info" :style="`height:` + ability_height + `px`">
		<view style="height: 1upx;"></view>
		<view class="school-card">
			<image class="school-logo" mode="aspectFit" src="@/static/logo.jpg" @error="imageError"></image>
			<view class="school-info">
				<text>山河大学</text>
				<view>
					<text>卓越工程师教育培养计划</text>
					<text>卓越整活人才教育培养计划</text>
				</view>
			</view>
		</view>
		<view class="ability-card">
			<view class="card-info" v-for="index in 9" :key="index">
				<text class="t-icon t-icon-keyan"></text>
				<text>山河名师</text>
			</view>
		</view>
		<view class="tips iconfont icon-shu-duidie">学校为虚拟大学，谨防诈骗</view>
	</view>
</template>

<script>
export default {
    data() {
        return {
            ability_height: "0",
        };
    },
    mounted() {
        uni.getSystemInfo({
            success: (res) => {
                this.ability_height = res.windowHeight;
            }
        });
    },
}
</script>

<style scoped>
.ability-info {
	background-color: #f3f5f8;
}

.school-card {
	display: flex;
	flex-direction: row;
	justify-content: flex-start;
	align-items: center;
	background-color: #fdfdfe;
	width: 95%;
	height: 25%;
	margin: 40upx auto;
	border-radius: 30upx;
}

.school-logo {
	width: 200upx;
	height: 200upx;
}
.school-info{
	margin-left: 20upx;
}

.school-info,.school-info view{
	display: flex;
	flex-direction: column;
    align-items: flex-start;
	margin-top: 10upx;
}
.school-info view text{
	color: #8a8b8c;
	background-color: #eaedf0;
	padding: 2upx 10upx;
	margin-top: 15upx;
	border-radius: 10upx;
}

.ability-card{
	width: 95%;
    height: 60%;
    margin: 40upx auto;
	margin-bottom: 20upx;
    background-color: #fdfdfe;
    border-radius: 30upx;
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-template-rows: 1fr 1fr 1fr;
	grid-gap: 20upx;
    justify-content: space-around;
    align-items: center;
    justify-items: center;
    align-content: space-around;
}

.card-info{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}
.card-info text:first-child{
	width: 100upx; 
    height: 100upx;
	margin-bottom: 10upx;
}
.card-info text:last-child{
	margin-top: 10upx;
}

.tips{
	width:95%;
	margin: 0 auto;
	text-align: center;
	color: red;
	font-size: smaller;
}

</style>
