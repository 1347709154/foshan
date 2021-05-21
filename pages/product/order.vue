<template>
	<view class="content">
		<!-- 选择取货方式 -->
		 <view class="collect">
			 <view class="address">
				 <view class="address-add">石阡县佛顶上景区店</view>
				 <view class="address-add" style="color: #6F6F6F;">距您321m</view>
				 <image src="../../static/home/dingwe-1.png"></image>
			 </view>
			 <view class="switch">
				 <view :class="[give_type==1?'switch-zi':'switch-type']"   @click="give(1)" >自提</view>
				 <view :class="[give_type==2?'switch-zi':'switch-type']" @click="give(2)">外卖</view>
			 </view>
		 </view>
		 <!-- 商品信息 -->
		 <view class="goods-box">
			 <view style="margin-top:15rpx ;margin-bottom: 20rpx;display: flex;flex-direction: row;">
				 <view class="goods-img">
				 	<image mode="aspectFit" src="https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg.yzcdn.cn%2Fupload_files%2F2015%2F05%2F18%2FFkpm67LDL8t0CXanGIyn5L9vaCcw.jpg%3FimageView2%2F2%2Fw%2F580%2Fh%2F580%2Fq%2F75%2Fformat%2Fjpg&refer=http%3A%2F%2Fimg.yzcdn.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1624001293&t=cd57513a819f22a9b626274984d6091a"></image>
				 </view>
				 <view class="goods-xinxi">
					 <view class="goods-name">
						 <view>【特产】铜仁石阡特产黄水粑4只装</view>
						 <view style="text-align: right;">￥ 26.0</view>
					 </view>
					 <view>X1</view>
				 </view>
			 </view>
			 <view style="" class="goods-yhq">
				 <view class="yhq">
					 <image src="../../static/home/yhq.png"></image>
					 <view>优惠券</view>
				 </view>
				 <view class="keyong">无可用</view>
			 </view>
			 <view class="goods-bottom">
				 <view class="shifu">
					 <view class="yhj">优惠 <text style="color: #E36C3E;font-weight: bold;">￥ 0</text></view>
				 </view>
				 <view class="fk">
					 实付：<text style="color: #000000;">￥ 0</text>
				 </view>
			 </view>
		 </view>
		 <!-- 支付选择 -->
		 <view class="pay-type">
			 <view class="type" @click="paytype(1)">
				 <view class="type-l">
					 <image src="../../static/home/WeChat.png"></image>
					 <view>微信</view>
				 </view>
				 <view class="type-r">
					 <radio value="1" :checked="pay_type==1" style="transform:scale(0.7)"  color="#09BB07"/>
				 </view>
			 </view>
			 <view class="type" @click="paytype(2)">
				 <view class="type-l">
					 <image src="../../static/home/Alipay.png"></image>
					 <view>支付宝</view>
				 </view>
				 <view class="type-r">
					 <radio value="2" :checked="pay_type==2" style="transform:scale(0.7)" color="#09BB07" />
				 </view>
			 </view>
		 </view>
		<!-- 协议 -->
		<view class="pay-xy">
			<radio value="" :checked="pay_xy" style="transform:scale(0.7)"  color="#09BB07" @click="payxy"/>
			<view>我已阅读并同意<text style="color: #3287FE;">《支付协议》</text></view>
		</view>
		<!-- 底部支付 -->
		<view class="bottom">
			<view class="bottom-num">
				￥<text style="font-weight: bold;font-size: 40rpx;">0.0</text>
			</view>
			<view class="toPay" @click="topay">去支付</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello',
				give_type:1,//配送方式
				pay_type:0,//支付方式
				pay_xy:false,//是否同意支付协议
				
			}
		},
		onLoad(options) {
			this.type= options.type
		},
		methods: {
			//配送方式
			give:function(e){
				let give_type= e;
				this.give_type= e;
				if(e==2){
					uni.navigateTo({
						url:"/pages/address/index?give_type=2" 
					})
				}
				
			},
			//支付选择
			paytype:function(e){
				this.pay_type=e;
			},
			//支付协议
			payxy:function(e){
				
				this.pay_xy=!this.pay_xy;
			},
			topay:function(e){
				let type= this.type;
				uni.navigateTo({
					url:"/pages/goodsinfo/gettiket?type=" +this.type
				})
			}
		}
	}
</script>

<style>
	page{
		background: #F2F5FA;
	}
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	/* 选择取货方式 */
	.collect{
		width: 96%;
		background: #FFFFFF;
		margin-top: 20rpx;
		border-radius: 15rpx;
		padding: 25rpx 20rpx;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
	}
	.address{
		position: relative;
	}
	.address-add{
		font-size: 28rpx;
		margin-top: 10rpx;
		margin-left: 50rpx;
		width: 400rpx;
		display: -webkit-box;
		-webkit-box-orient: vertical;
		-webkit-line-clamp: 1;
		overflow: hidden;
	}
	.address>image{
		position: relative;
		left: 0rpx;
		top: -70rpx;
		width: 40rpx;
		height: 40rpx;
	}
	.switch{
		background: #32B134;
		border-radius: 50rpx;
		padding: 4rpx 10rpx;
		display: flex;
		flex-direction: row;
	}
	.switch-zi{
		width: 100rpx;
		height: 80rpx;
		text-align: center;
		line-height: 80rpx;
		
		
		border-radius: 45%;
		background: #FFFFFF;
		color:#32B134 ;
		font-size: 28rpx;
	}
	.switch-type{
		width: 100rpx;
		height: 80rpx;
		line-height: 80rpx;
		text-align: center;
		color: #FFFFFF;
	}
	/* 商品信息 */
	.goods-box{
		width: 96%;
		background: #FFFFFF;
		margin-top: 20rpx;
		border-radius: 15rpx;
		display: flex;
		flex-direction: column;
		padding: 20rpx 20rpx 10rpx 20rpx;
		
	}
	.goods-img{
		width: 150rpx;
	}
	.goods-img>image{
		width: 100%;
		height: 100%;
	}
	.goods-xinxi{
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		align-items: flex-start;
		margin-left: 10rpx;
	}
	.goods-name{
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: flex-start;
	}
	.goods-name>view{
		width: 50%;
		font-size: 28rpx;
		font-weight: bold;
		margin-bottom: 10rpx;
	}
	.goods-yhq{
		display: flex;
		flex-direction: row;
		border-bottom: 1rpx solid #ddd;
		justify-content: space-between;
		align-items: flex-start;
		padding-bottom: 20rpx;
		font-size: 28rpx;
	}
	.yhq{
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
		padding-left: 20rpx;
	}
	.yhq>view{
		padding-left: 10rpx;
		font-size: 28rpx;
	}
	.yhq>image{
		width: 30rpx;
		height: 30rpx;
	}
	.keyong{
		font-size: 28rpx;
	}
	.goods-bottom{
		display: flex;
		flex-direction: row;
		justify-content: flex-end;
		height: 80rpx;
		line-height: 80rpx;
	}
	
	.yhj{
		font-size: 28rpx;
	}
	.fk{
		margin-left: 40rpx;
		font-size: 28rpx;
		color: #3B3B3B;
	}
	/* 支付选择 */
	.pay-type{
		width: 96%;
		background: #FFFFFF;
		border-radius: 15rpx;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		margin-top: 20rpx;
		padding: 20rpx 32rpx;
	}
	.type{
		width: 100%;
		height: 100rpx;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
	}
	.type-l{
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: flex-end;
	}
	.type-l>image{
		width: 55rpx;
		height: 55rpx;
	}
	.type-l>view{
		margin-left: 10rpx;
		font-size: 36rpx;
		font-weight: bold;
	}
	/* 协议 */
	.pay-xy{
		margin-top: 20rpx;
		width: 96%;
		display: flex;
		flex-direction: row;
		align-items: center;
		padding-left: 32rpx;
		font-size: 28rpx;
	}
	/* 底部支付 */
	.bottom{
		width: 100%;
		height: 120rpx;
		position: fixed;
		bottom: 0rpx;
		left: 0rpx;
		background: #FFFFFF;
		z-index: 999999;
		/* -webkit-box-shadow: 0px 0px 10px rgba(0,0,0,.8);
		  -moz-box-shadow: 0px 0px 10px rgba(0,0,0,.8);
		  box-shadow: 0px 0px 10px rgba(0,0,0,.8); */
		  display: flex;
		  flex-direction: row;
		  justify-content: space-between;
		  align-items: center;
		  padding: 20rpx 32rpx;
	}
	.bottom-num{
		font-size: 32rpx;
		
		padding-left: 20rpx;
	}
	.toPay{
		width: 250rpx;
		background: #FF0000;
		border-radius: 40rpx;
		height: 80rpx;
		line-height: 80rpx;
		text-align: center;
		color: #FFFFFF;
		
	}
</style>
