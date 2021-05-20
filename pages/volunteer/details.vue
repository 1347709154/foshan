<template>
	<view class="content">
		<!-- 志愿者信息 -->
		<view class="user-box">
			<view class="user-img">
				<image src="../../static/user/user_img.png" mode="aspectFit"></image>
			</view>
			<view class="user-xinxi">
				<view style="font-size: 28rpx;font-weight: bold;margin-bottom: 10rpx;">王甜</view>
				<view class="user-li">服务地区：景区</view>
				<view class="user-li">服务领域：帮困，文明指导，语言服务</view>
				<view class="user-li">特长能力：IT技术</view>
				<view class="user-li">行业领域：新时代文明实践志愿者</view>
			</view>
		</view>
		<!-- 分割线 -->
		<view class="lin"></view>
	   <!-- 任务介绍 -->
	   <view class="body">
		   <view class="jiesao">人物简介</view>
		   <view class="user-desc">
			   1939年出生，浙江镇海人。 现为上海中国画院一级美术师、中国书法家协会理事、上海书法家协会名誉主席、上海市文联副主席。 1962年 参加上海市青年宫书法学习班。得到沈尹默、拱德邻、翁闿运等著名书法家亲授。以节临米芾《蜀素贴》行书入选由上海中国书法篆刻研究会成立后第一次举办的上海市书法展览。 1965年 由书刻会选送作品参加“中国现代书法展览”。
		   </view>
	   </view>
	   
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	/* 志愿者信息 */
	.user-box{
		width: 94%;
		display: flex;
		flex-direction: row;
	}
	.user-img{
		width: 120rpx;
		height: 120rpx;
	}
	.user-img>image{
		width: 100%;
		height: 100%;
	}
	.user-xinxi{
		margin-left: 15rpx;
		display: flex;
		flex-direction: column;

	}
	.user-li{
		margin-top: 15rpx;
		font-size: 28rpx;
		color: #858585;
	}
	/* 分割线 */
	.lin{
		width: 100%;
		height: 15rpx;
		background: #EEEEEE;
		margin-top: 30rpx;
	}
	/* 任务介绍 */
	.body{
		width: 94%;
	}
	.jiesao{
		color: #15942D;
		margin-top: 30rpx;
		font-size: 32rpx;
		font-weight: bold;
	}
	.user-desc{
		font-size: 28rpx;
		color: #060606;
		margin-top: 40rpx;
	}
</style>
