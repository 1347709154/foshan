<template>
	<view class="content">
		<!-- 人物信息 -->
		<view class="top-card">
			<image src="../../static/touxiang.jpg" mode="aspectFill"></image>
			<view class="card-r">
				<view>薛定尔の猫</view>
				<view>102人已预约  |  从业4年  </view>
				<view>专业好·形象好·服务好</view>
			</view>
		</view>
		<!-- 任务介绍 -->
		<view class="desc">
			<view class="shanchang">
				<text style="font-weight: bold;">擅长：</text>
				喵喵喵喵喵喵喵喵喵喵
			</view>
			<view class="shanchang">
				<text style="font-weight: bold;">介绍：</text>
				短短的六天时间，有幸见识了祖国最美的风景。九寨、黄龙、峨眉山、乐山景色各有千秋。更有幸的认识了星星，让我们吃的好，住的好，车也好，最主要玩的好，景区游玩时间充足，线路安排合理。开心之余还能省钱，实属难得
			</view>
		</view>
		<!-- 底部按钮 -->
		<view class="bottom">
			<view class="bottom-l">
				<view class="bottom-x">
					<view>
						<image src="../../static/home/dianzan.png"></image>
						<view>收藏</view>
					</view>
					<view>
						<image src="../../static/home/kefu.png"></image>
						<view>客服</view>
					</view>
				</view>
			</view>
			<view class="bottom-r">
				<view class="fenxiang">
					<view style="margin-right: 5rpx;">分享</view>
					<u-icon  size="45" name="share"></u-icon>
				</view>
				<view class="yy" @click="topay">
					<view>预约</view>
				</view>
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
			//跳转支付
			topay:function(e){
				uni.navigateTo({
					url:"/pages/guide-pre/pre"
				})
			}
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
	/* 人物信息 */
	.top-card{
		background: url('../../static/banner.png');
		background-size: 100% 100%;
		width: 100%;
		height: 300rpx;
		padding: 30rpx;
		display: flex;
		flex-direction: row;
	}
	.top-card>image{
		width: 180rpx;
		height: 180rpx;
		border-radius: 50%;
	}
	.card-r{
		display: flex;
		flex-direction: column;
		margin-left: 15rpx;
	}
	.card-r>view{
		margin-top: 15rpx;
		font-size: 28rpx;
		color: #FFFFFF;
	}
	/* 人物介绍 */
	.desc{
		width: 100%;
		min-height: 500rpx;
		border-radius: 35rpx 35rpx 0  0;
		margin-top: -60rpx;
		background: #FFFFFF;
		padding: 20rpx 32rpx;
	}
	.shanchang{
		margin-top: 20rpx;
		font-size: 30rpx;
	}
	/* 底部按钮 */
	.bottom{
		width: 100%;
		height: 120rpx;
		position: fixed;
		bottom: 0rpx;
		left: 0rpx;
		/* background: #007AFF; */
		background: #FFFFFF;
		z-index: 999999;
		-webkit-box-shadow: 0px 0px 10px rgba(0,0,0,.8);
		  -moz-box-shadow: 0px 0px 10px rgba(0,0,0,.8);
		  box-shadow: 0px 0px 10px rgba(0,0,0,.8);
		  display: flex;
		  flex-direction: row;
	}
	.bottom-l{
		display: flex;
		flex-direction: row;
	}
	.bottom-x{
		display: flex;
		flex-direction: row;
		
	}
	.bottom-x>view{
		width: 120rpx;
		height: 120rpx;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}
	.bottom-x>view>image{
		width: 60rpx;
		height: 60rpx;
	}
	.bottom-r{
		width: 630rpx;
		height: 120rpx;
		display: flex;
		flex-direction: row;
	}
	.fenxiang{
		width: 50%;
		height: 120rpx;
		background: #000000;
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
		color: #FFFFFF;
		font-size: 32rpx;
	}
	.yy{
		width: 50%;
		height: 120rpx;
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
		background: #E50505;
		color: #FFFFFF;
		font-size: 32rpx;
	}
</style>
