<template>
	<view class="content">
		<view class="add" @click="add">+新增地址</view>
		<view class="add-list">
			<view class="add-list-l">
				<view class="add-list-l-top">
					<image src="../../static/user/dingwei.png" mode="aspectFit"></image>
					<view>收货人：李海欣</view>
					<view>136 8888 6666</view>
				</view>
				<view class="add-list-l-bottom">收货地址：四川省-成都市-龙泉驿区-大面镇
					成龙大道师大现代花园12栋2单元
				</view>
			</view>
			<view class="add-list-r">
				<view>
					<image src="../../static/user/address-up.png" mode="aspectFit"></image>
				</view>
			</view>
		</view>
		<view class="add-list">
			<view class="add-list-l" @click="give">
				<view class="add-list-l-top">
					<image src="../../static/user/dingwei.png" mode="aspectFit"></image>
					<view>收货人：李海欣</view>
					<view>136 8888 6666</view>
				</view>
				<view class="add-list-l-bottom">收货地址：四川省-成都市-龙泉驿区-大面镇
					成龙大道师大现代花园12栋2单元
				</view>
			</view>
			<view class="add-list-r">
				<view>
					<image src="../../static/user/address-up.png" mode="aspectFit"></image>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				give_type:''//判断是否为配送页面跳转过来
			}
		},
		onLoad(options){
			this.give_type=options.give_type;
		},
		methods: {
			//添加地址
			add:function(e){
				uni.navigateTo({
					url:"/pages/address/add"
				})
			},
			//返回配送页面
			give:function(e){
				uni.navigateBack({
					
				})
			}
		}
	}
</script>

<style>
	page{
		background: #E4E7EE;
	}
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	.add{
		
		background: #ffffff;
		height: 100rpx;
		width: 96%;
		line-height: 100rpx;
		text-align: center;
		font-size: 32rpx;
		color: #2AA5FF;
		font-weight: bold;
		margin-top: 30rpx;
		border-radius: 15rpx;
	}
	.add-list{
		margin-top: 20rpx;
		background: #ffffff;
		width: 96%;
		border-radius: 15rpx;
		padding: 0rpx 32rpx;
		display: flex;
		flex-direction: row;
	}
	.add-list-l{
		display: flex;
		flex-direction: column;
		width: 85%;
	}
	.add-list-l-top{
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: flex-start;
		margin-top: 30rpx;
	}
	.add-list-l-top>image{
		width: 35rpx;
		height: 35rpx;
		margin-right: 10rpx;
	}
	.add-list-l-top>view{
		font-size: 28rpx;
		margin-right: 10rpx;
	}
	.add-list-l-bottom{
		font-size: 28rpx;
		color: #666666;
		margin-top: 20rpx;
	}
	.add-list-r{
		width: 25%;
		padding: 50rpx 0rpx;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}
	.add-list-r>view{
		margin-top: 30rpx;
		border-left: 2rpx solid #ddd;
	}
	.add-list-r>view>image{
		margin-left: 20rpx;
		width: 60rpx;
		height: 60rpx;
		font-weight: bold;
	}
</style>
