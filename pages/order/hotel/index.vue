<template>
	<view class="content">
		<!-- 顶部导航 -->
		<view class="nav">
			<view @click="change(0)" class="nav-ul"><text :class="[btnnum=='0'?'active':'text']">全部</text></view>
			<view @click="change(1)" class="nav-ul"><text :class="[btnnum==1?'active':'text']">待付款</text></view>
			<view @click="change(2)" class="nav-ul"><text :class="[btnnum==2?'active':'text']">待使用</text></view>
			<view @click="change(3)" class="nav-ul"><text :class="[btnnum==3?'active':'text']">待评价</text></view>
			<view @click="change(4)" class="nav-ul"><text :class="[btnnum==4?'active':'text']">已完成</text></view>
		</view>
		<!-- 订单列表 -->
		<view class="order-box">
			<view class="order-list" v-for="(item,index) in order" :key="index">
				<view class="order-list-top">
					<view class="order-img">
						<image :src="item.hotel_logo"></image>
						<view>{{item.hotel_name}}</view>
					</view>
					<view class="order-state" style="color: #FF0000;" v-if="item.state==1||item.state==3">支付完成</view>
					<view class="order-state" style="color: #FF0000;" v-if="item.state==2">待付款</view>
					<view class="order-state" style="color: #FF0000;" v-if="item.state==4">待评价</view>
					<view class="order-state" style="color: #FF0000;" v-if="item.state==5">交易完成</view>
				</view>
				<view class="order-list-zj">
					<view class="order-list-goodsimg">
						<image :src="item.hotel_img" mode="aspectFill"></image>
					</view>
					<view class="order-list-desc">
						<view>{{item.hotel_number}}张,{{item.hotel_type}}</view>
						<view>{{item.hotel_time}}</view>
						<view>总价：￥{{item.money}}</view>
					</view>
				</view>
				<view class="order-list-bottom" v-if="item.state==1||item.state==3">
					<view class="gaiqian" style="border: 1rpx solid #E2E1E1;color: #131313;">申请发票</view>
					<view class="gaiqian">改签</view>
					<view class="shiyong">去使用</view>
				</view>
				<view class="order-list-bottom" v-if="item.state==2">
					<view class="gaiqian" style="border: 1rpx solid #E2E1E1;color: #131313;">取消订单</view>
					<view class="shiyong" style="background: #FF0000;" @click="topay">去支付</view>
				</view>
				<!-- <view class="order-list-bottom" v-if="item.state==3">
					<view class="gaiqian" style="border: 1rpx solid #E2E1E1;color: #131313;">申请发票</view>
					<view class="gaiqian" style="border: 1rpx solid #E2E1E1;color: #131313;">改签</view>
					<view class="shiyong">去使用</view>
				</view> -->
				<view class="order-list-bottom" v-if="item.state==4">
					<view class="gaiqian" style="border: 1rpx solid #E2E1E1;color: #131313;">申请发票</view>
					<view class="gaiqian" style="border: 1rpx solid #E2E1E1;color: #131313;">再来一单</view>
					<view class="shiyong" style="background: #FF0000;">评价</view>
				</view>
				<view class="order-list-bottom" v-if="item.state==5">
					<view class="gaiqian" style="border: 1rpx solid #E2E1E1;color: #131313;">申请发票</view>
					<view class="gaiqian" style="border: 1rpx solid #E2E1E1;color: #131313;">再来一单</view>
				</view>
			</view>	
		</view>
		<!-- 去支付弹窗 -->
		<u-popup v-model="show" :closeable="true" mode="bottom" width="100%">
			<!-- 支付选择 -->
			<view class="pay-type">
				 <view class="type" @click="paytype(1)">
					 <view class="type-l">
						 <image src="../../../static/home/WeChat.png"></image>
						 <view>微信</view>
					 </view>
					 <view class="type-r">
						 <radio value="1" :checked="pay_type==1" style="transform:scale(0.7)"  color="#09BB07"/>
					 </view>
				 </view>
				 <view class="type" @click="paytype(2)">
					 <view class="type-l">
						 <image src="../../../static/home/Alipay.png"></image>
						 <view>支付宝</view>
					 </view>
					 <view class="type-r">
						 <radio value="2" :checked="pay_type==2" style="transform:scale(0.7)" color="#09BB07" />
					 </view>
				 </view>
			</view>
			<view class="Submit" @click="Submit">支付</view>
		</u-popup>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				show:false,
				btnnum: '0',
				pay_type:0,//支付方式
				pay_xy:false,//是否同意支付协议
				type:'',//支付类型
				order:[
						{
						hotel_logo:"../../../static/user/logo.png",
						hotel_name:"佛顶山生态旅游景区门票",
						state:1,
						hotel_img:"../../../static/banner.png",
						hotel_number:2,
						hotel_type:"大床房",
						hotel_time:"2020-5-19 14:43:59",
						money:100
					},
					{
						hotel_logo:"../../../static/user/logo.png",
						hotel_name:"佛顶山生态旅游景区门票",
						state:2,
						hotel_img:"../../../static/banner.png",
						hotel_number:2,
						hotel_type:"大床房",
						hotel_time:"2020-5-19 14:43:59",
						money:100
					},
					{
						hotel_logo:"../../../static/user/logo.png",
						hotel_name:"佛顶山生态旅游景区门票",
						state:3,
						hotel_img:"../../../static/banner.png",
						hotel_number:2,
						hotel_type:"大床房",
						hotel_time:"2020-5-19 14:43:59",
						money:100
					},
					{
						hotel_logo:"../../../static/user/logo.png",
						hotel_name:"佛顶山生态旅游景区门票",
						state:4,
						hotel_img:"../../../static/banner.png",
						hotel_number:2,
						hotel_type:"大床房",
						hotel_time:"2020-5-19 14:43:59",
						money:100
					},
					{
						hotel_logo:"../../../static/user/logo.png",
						hotel_name:"佛顶山生态旅游景区门票",
						state:5,
						hotel_img:"../../../static/banner.png",
						hotel_number:2,
						hotel_type:"大床房",
						hotel_time:"2020-5-19 14:43:59",
						money:100
					}
				]
			}
		},
		onLoad() {

		},
		methods: {
			// 顶部导航切换
			change(e) {
				
				this.btnnum = e
				 console.log(this.btnnum)
			},
			//去支付
			topay:function(e){
				this.show = true;
			},
			//支付选择
			paytype:function(e){
				this.pay_type=e;
			},
			Submit:function(e){
				if(!this.pay_type){
					uni.showToast({
					    title: '请选择支付方式',
					    duration: 2000,
						icon:'none'
					});
				}else{
					
				}
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
/* 顶部导航 */
	.nav{
		position: fixed;
		top: 44px;
		left: 0rpx;
		height: 100rpx;
		width: 100%;
		z-index: 1;
		background: #ffffff;
	}
	.nav-ul{
		float: left;
		width: 20%;
		height: 100rpx;
		text-align: center;
	}
	.nav-ul>.text{
		display: inline-block;
		color: #676767;
		height: 100rpx;
		font-size: 32rpx;
		font-weight: bold;
		line-height: 100rpx;
	}
	.active{
		display: inline-block;
		font-size: 32rpx;
		height: 96rpx;
		line-height: 98rpx;
		color: #32B134;
		font-weight: bold;
		border-bottom: 4rpx solid #32B134;
	}
	/* 订单列表 */
	.order-box{
		margin-top: 100rpx;
		width: 94%;
		display: flex;
		flex-direction: column;
		padding-bottom: 30rpx;
	}
	.order-list{
		width:100%;
		background: #ffffff;
		margin-top: 30rpx;
		border-radius: 25rpx;
		display: flex;
		flex-direction: column;
		padding: 32rpx;
	}
	.order-list-top{
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: flex-start;
		border-bottom: 1rpx solid #ddd;
		padding-bottom: 20rpx;
		margin-top: 10rpx;
	}
	.order-img{
		display: flex;
		flex-direction: row;
	}
	.order-img>image{
		width: 45rpx;
		height: 45rpx;
	}
	.order-img>view{
		margin-left: 10rpx;
	}
	.order-list-zj{
		display: flex;
		flex-direction: row;
		margin-top: 20rpx;
	}
	.order-list-goodsimg{
		width: 165rpx;
		height: 165rpx;
	}
	.order-list-goodsimg>image{
		width: 100%;
		height: 100%;
		border-radius: 15rpx;
	}
	.order-list-desc{
		margin-left: 15rpx;
	}
	.order-list-desc>view{
		height: 55rpx;
		line-height: 55rpx;
		color: #010101;
		font-size: 30rpx;
	}
	.order-list-bottom{
		display: flex;
		flex-direction: row;
		justify-content: flex-end;
		align-items: flex-end;
		margin-top: 15rpx;
	}
	.gaiqian{
		border: 1rpx solid #C1E7C2;
		color: #5CBD5D;
		padding: 2rpx 15rpx;
		font-size: 28rpx;
		border-radius: 8rpx;
		margin-right: 25rpx;
	}
	.shiyong{
		background: #32B134;
		color: #fff;
		padding: 2rpx 15rpx;
		font-size: 28rpx;
		border-radius: 8rpx;
		margin-right: 15rpx;
	}
	/* 支付选择 */
	.pay-type{
		width: 96%;
		background: #FFFFFF;
		border-radius: 15rpx;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		margin-top: 50rpx;
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
		width: 45rpx;
		height: 45rpx;
	}
	.type-l>view{
		margin-left: 10rpx;
		font-size: 30rpx;
		font-weight: bold;
	}
	.Submit{
		margin-top: 20rpx;
		height: 80rpx;
		line-height: 80rpx;
		background:#FF9726 ;
		color: #FFFFFF;
		text-align: center;
		font-size: 32rpx;
	}
</style>
