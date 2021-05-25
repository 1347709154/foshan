<template>
	<view class="content">
		<view class="pin">
			<!-- <u-icon name="close-circle-fill" color="#FF2F61" size="48"></u-icon> -->
			<u-icon name="checkmark-circle-fill" color="#FF2F61" size="48"></u-icon>
			<view>拼团成功</view>
			<!-- <view>拼团失败</view> -->
		</view>
		<view class="pin-tel">商家按照付款顺序发货中，请耐心等待！</view>
		<!-- <view class="pin-tel" style="color: #FF6247;">不要灰心，再接再厉哦！</view> -->
		<view class="pin-bt">去首页逛逛</view>
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
	page{
		background: #F4F4F4;
	}
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	.pin{
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
		font-size: 38rpx;
		font-weight: bold;
		color: #FF2F61;
		margin-top: 50rpx;
	}
	.pin>view{
		margin-left: 10rpx;
	}
	.pin-tel{
		margin-top: 20rpx;
		font-size: 32rpx;
		font-weight: bold;
		color: #B9B8B8;
	}
	.pin-bt{
		height: 80rpx;
		width: 90%;
		line-height: 80rpx;
		text-align: center;
		background:linear-gradient(to right, #FF6247,#FF2F61);
		color: #FFFFFF;
		font-size: 32rpx;
		margin-top: 30rpx;
		border-radius: 20rpx;
	}
</style>
