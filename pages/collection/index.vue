<template>
	<view class="content">
		<!-- 收藏列表 -->
	<view class="list">
		<view class="list-l">
			<view style="margin-top: 25rpx;font-size: 32rpx;font-weight: bold;">金山雪海一日游</view>
			<view style="width: 95%;margin-top: 30rpx;font-size: 30rpx;overflow: hidden;
	text-overflow:ellipsis;white-space: nowrap;">金山雪海一日游金山雪海金山金山雪海一日游金山雪海金山</view>
			<view style="width: 95%;margin-top: 30rpx;font-size: 32rpx;color: #8A8E99;">金山雪海一日游金山雪海金山</view>
		</view>
		<view class="list-r">
			<image src="../../static/banner.png" mode="scaleToFill"></image>
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
	page{
		background: #F2F6F7;
	}
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	.list{
		width: 94%;
		margin-top: 20rpx;
		background: #FFFFFF;
		border-radius: 20rpx;
		padding: 25rpx 15rpx;
		display: flex;
		flex-direction: row;
	}
	.list-l{
		width: 68%;
		display: flex;
		flex-direction: column;
		overflow: hidden;
		text-overflow:ellipsis;
		white-space: nowrap;
		margin-right: 10rpx;
	}
	.list-r{
		width: 30%;
		text-align: right;
	}
	.list-r>image{
		width: 210rpx;
		height: 200rpx;
		border-radius: 15rpx;
	}
</style>
