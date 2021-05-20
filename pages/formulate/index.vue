<template>
	<view class="content">
		<view class="card">
			<image src="../../static/banner.png" mode="widthFix"></image>
			<view>金山雪海一日游</view>
		</view>
		<view class="card">
			<image src="../../static/banner.png" mode="widthFix"></image>
			<view>金山雪海一日游</view>
		</view>
		<view class="null">没有更多了~</view>
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
	.card{
		box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
		transition: 0.3s;
		width: 96%;
		border-radius: 5px;
		padding-bottom: 30rpx;
		margin-bottom: 30rpx;
	}
	.card>image{
		width: 100%;
		height: 400rpx;
		border-radius: 5px 5px 0rpx 0rpx;
	}
	.card>view{
		padding-left: 32rpx;
		margin-top: 20rpx;
		font-size: 32rpx;
		font-weight: bold;
	}
	.null{
		margin-top: 30rpx;
		width: 100%;
		text-align: center;
		font-size: 30rpx;
		color: #575757;
	}
</style>
