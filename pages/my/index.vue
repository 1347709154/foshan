<template>

	<view class="header">
		<!-- 个人信息 -->
		<view class="header_block">
			<image src="../../static/banner.png" mode="scaleToFill" class="header_block_img"></image>
			<view class="header_block_title">
				<view class="header_block_title_te">我的</view>
				<image src="../../static/user/set.png" mode="scaleToFill" class="set"></image>
			</view>
			<view class="user-o">
				<view class="user-img">
					<image src="../../static/user/user_img.png" mode="scaleToFill"></image>
				</view>
				<view class="user-message">
					<view class="user-name">彩云之南</view>
					<view class="user_tel">88888888888</view>
				</view>
				<button class="button-yuanjiao" hover-class="bg-click" @tap="bianji">编辑资料</button>
				<!-- <view class="user-btn">编辑资料</view> -->
			</view>
			<!-- 积分管理 -->
			<view class="integral">
				<view class="integral-fen">
					<text style="margin-right: 15rpx;font-size: 32rpx;">我的积分</text>
					1000
				</view>
				<view class="integral_bt" @click="jifen">
					<view>积分管理</view>
					<u-icon name="arrow-right" color="#ffffff" size="28"></u-icon>
				</view>
			</view>
		</view>
		<!-- 主页、收藏、优惠券 -->
		<view class="card">
			<view class="card-ul" @click="shoucang">
				<view style="font-size: 40rpx;font-weight: bold;">
					<image src="../../static/user/shoucang.png" style="width: 50rpx;height: 50rpx;"></image>
				</view>
				<view style="margin-top: 20rpx;font-size: 32rpx;">收藏</view>
			</view>
			<view class="card-ul">
				<view style="font-size: 40rpx;font-weight: bold;">
					<image src="../../static/user/zhuye.png" style="width: 50rpx;height: 50rpx;"></image>
				</view>
				<view style="margin-top: 20rpx;font-size: 32rpx;">我的主页</view>
			</view>
			<view class="card-ul" @click="footprint">
				<view style="font-size: 40rpx;font-weight: bold;">
					<image src="../../static/user/zuji.png" style="width: 50rpx;height: 50rpx;"></image>
				</view>
				<view style="margin-top: 20rpx;font-size: 32rpx;">足迹</view>
			</view>
		</view>
		<!-- 订单 -->
		<view class="order-card">
			<view class="order-top">
				<view class="" style="font-size: 38rpx;font-weight: bold;">我的订单</view>
				<view class="">全部订单</view>
			</view>
			<view class="order-bottom">
				<view class="order-bottom-ul">
					<image src="../../static/user/payment.png" style="width: 75rpx;height: 55rpx;" mode="scaleToFill"></image>
					<view style="margin-top: 15rpx;font-size: 32rpx;">待付款</view>
				</view>
				<view class="order-bottom-ul">
					<image src="../../static/user/deliver.png" style="width: 75rpx;height: 55rpx;" mode="scaleToFill"></image>
					<view style="margin-top: 15rpx;font-size: 32rpx;">待发货</view>
				</view>
				<view class="order-bottom-ul">
					<image src="../../static/user/collect.png" style="width: 75rpx;height: 55rpx;" mode="scaleToFill"></image>
					<view style="margin-top: 15rpx;font-size: 32rpx;">待收货</view>
				</view>
				<view class="order-bottom-ul">
					<image src="../../static/user/review.png" style="width: 75rpx;height: 55rpx;" mode="scaleToFill"></image>
					<view style="margin-top: 15rpx;font-size: 32rpx;">待评论</view>
				</view>
				<view class="order-bottom-ul">
					<image src="../../static/user/shouhou.png" style="width: 75rpx;height: 55rpx;" mode="scaleToFill"></image>
					<view style="margin-top: 15rpx;font-size: 32rpx;">售后/退</view>
				</view>
			</view>
		</view>
		<!-- 底部功能 -->
		<view class="bottom-card">
			<view class="bottom-card-ul" @click="youhuiquan">
				<image src="../../static/user/youhuiquan.png" style="width: 50rpx;height: 50rpx;" mode="scaleToFill"></image>
				<view style="margin-top: 20rpx;font-size: 30rpx;">优惠券</view>
			</view>
			<view class="bottom-card-ul" @click="shimingrenzheng">
				<image src="../../static/user/shiming.png" style="width: 50rpx;height: 50rpx;" mode="scaleToFill"></image>
				<view style="margin-top: 20rpx;font-size: 30rpx;">实名认证</view>
			</view>
			<view class="bottom-card-ul">
				<image src="../../static/user/dizhi.png" style="width: 50rpx;height: 50rpx;" mode="scaleToFill"></image>
				<view style="margin-top: 20rpx;font-size: 30rpx;">地址管理</view>
			</view>
			<view class="bottom-card-ul" @click="invoice">
				<image src="../../static/user/fapiao.png" style="width: 50rpx;height: 50rpx;" mode="scaleToFill"></image>
				<view style="margin-top: 20rpx;font-size: 30rpx;">发票管理</view>
			</view>
			<view class="bottom-card-ul">
				<image src="../../static/user/zhibo.png" style="width: 50rpx;height: 50rpx;" mode="scaleToFill"></image>
				<view style="margin-top: 20rpx;font-size: 30rpx;">直播好货</view>
			</view>
			<view class="bottom-card-ul">
				<image src="../../static/user/fenxiao.png" style="width: 50rpx;height: 50rpx;" mode="scaleToFill"></image>
				<view style="margin-top: 20rpx;font-size: 30rpx;">分销商</view>
			</view>
			<view class="bottom-card-ul">
				<image src="../../static/user/kefu.png" style="width: 50rpx;height: 50rpx;" mode="scaleToFill"></image>
				<view style="margin-top: 20rpx;font-size: 30rpx;">客服中心</view>
			</view>
			<view class="bottom-card-ul" @click="zhanghaoguanli">
				<image src="../../static/user/zhanghao.png" style="width: 50rpx;height: 50rpx;" mode="scaleToFill"></image>
				<view style="margin-top: 20rpx;font-size: 30rpx;">账号管理</view>
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
			//编辑资料
			bianji:function(e){
				uni.navigateTo({
					url:"../personal/index"
				})
			},
			//积分管理
			jifen:function(e){
				uni.navigateTo({
					url:"/pages/jifen/index"
				})
			},
			//收藏
			shoucang:function(e){
				uni.navigateTo({
					url:"../collection/index"
				})
			},
			//我的足迹
			footprint:function(e){
				uni.navigateTo({
					url:"/pages/footprint/index"
				})
			},
			//优惠券
			youhuiquan:function(e){
				uni.navigateTo({
					url:"/pages/youhuanquan/index"
				})
			},
			//实名认证
			shimingrenzheng:function(e){
				uni.navigateTo({
					url:"/pages/shimingrenzheng/index"
				})
			},
			//发票管理
			invoice:function(e){
				uni.navigateTo({
					url:"../invoice/index"
				})
			},
			//账号管理
			zhanghaoguanli:function(e){
				uni.navigateTo({
					url:"/pages/zhanghaoguanli/index"
				})
			}
		}
	}
</script>

<style>
	page {
		width: 100%;
		height: 100%;
		background-color: #F2F6F7;
	}

	.header {
		width: 100%;
	}

	.header_block>.header_block_img {
		position: absolute;
		left: 0;
		top: 0;
		width: 100%;
		height: 450rpx;
		z-index: 1;
	}

	.header_block_title {
		position: absolute;
		z-index: 1;
		height: 100rpx;
		width: 100%;
		padding-left: 32rpx;
		padding-right: 32rpx;
		line-height: 100rpx;
		text-align: center;
		/* background: #007AFF; */

	}

	.header_block_title_te {
		color: #FFFFFF;
		font-size: 42rpx;
		font-family: 'SimHei';
	}

	.set {
		width: 45rpx;
		height: 45rpx;
		position: absolute;
		z-index: 1;
		right: 32rpx;
		top: 30rpx;
	}

	.user-o {
		position: absolute;
		z-index: 1;
		padding-left: 32rpx;
		padding-right: 32rpx;
		/* background: #3F536E; */
		width: 100%;
		height: 200rpx;
		top: 100rpx;
	}

	.user-img {
		float: left;
		width: 150rpx;
		height: 150rpx;
		background: #FFFFFF;
		border-radius: 50%;
		margin-top: 10rpx;
	}

	.user-img>image {
		float: left;
		width: 150rpx;
		height: 150rpx;
		border-radius: 50%;
	}

	.user-message {
		display: inline-block;
		height: 200rpx;
	}

	.user-name {
		margin-left: 20rpx;
		margin-top: 5rpx;
		height: 100rpx;
		line-height: 100rpx;
		font-size: 40rpx;
		color: #ffffff;
	}

	.user_tel {
		margin-left: 20rpx;
		font-size: 36rpx;
		color: #ffffff;
	}
	.button-yuanjiao {
		float: right;
		height: 60rpx;
		line-height: 60rpx;
		width: 180rpx;
		margin-top: 60rpx;
		border-radius: 45rpx;
		color: #FFFFFF;
		background:linear-gradient(to right, #FFDE6E,#FF9726);
		font-size: 28rpx;
	}
	/* 积分管理 */
	.integral {
		position: absolute;
		top: 270rpx;
		width: 100%;
		height: 100rpx;
		z-index: 1;
		display: flex;
		flex-direction: row;
		padding-left: 48rpx;
	}

	.integral-fen {
		/* float: left; */
		width: 65%;
		overflow: hidden;
		line-height: 100rpx;
		color: #FFFFFF;
		font-size: 40rpx;

	}

	.integral_bt {
		/* float: right; */
		width: 35%;
		display: flex;
		flex-direction: row;
		line-height: 100rpx;
		text-align: right;
		/* align-self: auto;
		align-content:space-around */

	}

	.integral_bt>view {
		color: #FFFFFF;
		padding-left: 30rpx;
	}

	/* 收藏、我的、优惠券 */
	.card {
		position: absolute;
		width: 94%;
		margin-left: 3%;
		top: 390rpx;
		z-index: 1;
		height: 180rpx;
		background: #FFFFFF;
		border-radius: 30rpx;
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: center;

	}

	.card-ul {
		height: 100%;
		width: 100%;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	/* 订单 */
	.order-card{
		position: absolute;
		width: 94%;
		margin-left: 3%;
		top: 600rpx;
		z-index: 1;
		height: 250rpx;
		background: #FFFFFF;
		border-radius: 30rpx;
		display: flex;
		flex-direction: column;
		/* align-items: center;
		justify-content: center; */
	}
	.order-top{
		height: 80rpx;
		line-height: 80rpx;
		width: 100%;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		padding: 0rpx 40rpx;
	}
	.order-bottom{
		height: 150rpx;
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: center;
	}
	.order-bottom-ul{
		width: 20%;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	/* 底部功能 */
	.bottom-card{
		position: absolute;
		top:880rpx;
		z-index: 1;
		height: 300rpx;
		width: 100%;
		background: #ffffff;
		/* display: flex;
		flex-direction: row; */
		}
	.bottom-card-ul{
		float: left;
		width: 25%;
		height: 150rpx;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
</style>
