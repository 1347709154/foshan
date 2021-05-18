<template>
	<view class="content">
		<view class="bgimg">
			<image src="../../static/scenic/gou2.jpg" mode=""></image>
		</view>
		<view class="addrbox">
			<p id="p1">{{title}}</p>
			<p id="p2">{{level}}</p>
			<view class="locbox">
				<view class="leftaddr left">
					{{addr}}
				</view>
				<view class="map right" @tap="gomap">
					<a href="http://uri.amap.com/marker?position=106.70068384667965,26.57849601545628&name=花果园&coordinate=gaode&callnative=1">地图导航	> </a>
				</view>
			</view>
		</view>
		<view class="copn" v-for="item in cponlist">
			<span class="left">优惠</span>
			<view class="left money" >
				{{item}}
			</view>
			<view class="right getcpon">
				领券	>
			</view>
		</view>
		<p id="p3">门票</p>
		<view class="titektlist">
			<view class="list-item" v-for="item in titektlist">
				<view class="left info">
					<p id="title">{{item.title}}</p>
					<p class="keywords"><span v-for="items in item.keywords">{{items}}</span></p>
					<p id="sell">已售{{item.sell}}+</p>
				</view>
				<view class="right price">
					<view class="topprice">
						¥{{item.price}}
					</view>
					<view class="btns" @tap="creatorder">
						预订
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title:'佛顶山生态旅游景区（4A）',
				level:'4A级旅游景区',
				addr:'贵州省铜仁市石阡县西南缘与黔东南州施秉县交界处',
				cponlist:[
					"满100减5",
					"满30减3"
				],
				titektlist:[
					{
						title:'景区门票+旅游巴士+观光车票',
						price:300,
						sell:"1.5万",
						keywords:["退款无忧","无需换票"]
					},
					{
						title:'景区门票+旅游巴士',
						price:260,
						sell:"1.5万",
						keywords:["退款无忧","无需换票"]
					},
					{
						title:'景区门票+观光车票',
						price:200,
						sell:"1.5万",
						keywords:["退款无忧","无需换票"]
					},
					{
						title:'景区门票',
						price:150,
						sell:"1.5万",
						keywords:["退款无忧","无需换票"]
					},
					{
						title:'旅游巴士',
						price:100,
						sell:"1.5万",
						keywords:["退款无忧","无需换票"]
					},
					{
						title:'观光车票',
						price:100,
						sell:"1.5万",
						keywords:["退款无忧","无需换票"]
					}
				]
			};
		},
		methods:{
			// 跳转生成订单
			creatorder(){
				uni.navigateTo({
					url:"./submitorder"
				})
			}
		}
	}
</script>

<style lang="scss">
	page{
			background: #f1f1f1;
	}
	.bgimg {
		width: 100%;
		height: 631rpx;

		image {
			width: 100%;
			height: 100%;
		}
	}

	.addrbox {
		padding: 0 40rpx;
		width: 100%;
		height: 271rpx;
		border-radius: 51rpx 51rpx 0 0;
		background: #FFFFFF;
		margin-top: -100rpx;
		z-index: 2;
	}
	#p1{
		font-size: 36rpx;
		margin-top: 33rpx;
	}
	#p2{
		font-size: 24rpx;
		margin-top: 33rpx;
		color:#32B134 ;
	}
	.locbox{
		margin-top: 50rpx;
		height: 53rpx;
		width: 100%;
	}
	.leftaddr{
		width: 479rpx;
		font-size: 24rpx;
	}
	.map{
		// width: 80rpx;
		color: #327AB1;
		font-size: 20rpx;
		height: 20rpx;
	}
	a{
		text-decoration: none;
		color: #327AB1;
		font-size: 20rpx;
	}
	.copn{
		width: 726rpx;
		height: 64rpx;
		line-height: 63rpx;
		margin: auto;
		background: #FFFFFF;
		margin-top: 7rpx;
		padding: 0 27rpx;
		font-size: 24rpx;
	}
	.money{
		width: 116rpx;
		height: 31rpx;
		background: #EF1E22;
		color: #FFFFFF;
		font-size: 20rpx;
		margin-top: 15rpx;
		line-height: 31rpx;
		text-align: center;
		border-radius: 7rpx;
		margin-left: 20rpx;
	}
	.getcpon{
		font-size: 20rpx;
		color: #EF1E22;
	}
	#p3{
		margin-top: 30rpx;
		text-align: left;
		width: 100%;
		
		display: block;
		font-size: 28rpx;
		color: #000000;
		margin-left: 80rpx;
		font-weight: bold;
	}
	.titektlist{
		width: 726rpx;
		min-height: 200rpx;
		height: auto;
		background: #FFFFFF;
		border-radius: 7rpx;
		margin-top: 20rpx;
		padding: 0 27rpx;
	}
	.list-item{
		height: 134rpx;
		border-bottom: 1px solid #E5E5E5;
		width: 100%;
	}
	.list-item:last-of-type{
		margin-bottom: 30rpx;
		border-bottom: none;
	}
	.topprice{
		text-align: center;
		color: #EF1E22;
		font-size: 30rpx;
		margin-top: 30rpx;
	}
	.btns{
		width: 90rpx;
		height: 37rpx;
		text-align: center;
		line-height: 37rpx;
		color: white;
		font-size: 24rpx;
		background: #EF1E22;
		border-radius: 19rpx;
	}
	#title{
		margin-top: 20rpx;
	}
	.keywords{
		// margin-top: 5px;
		span{
			color: #327AB1;
			font-size: 18rpx;
			display: inline-block;
			width: 60px;
			border-right: 1px solid #327AB1;
			margin-right: 20rpx;
		}
		span:last-of-type{
			border-right:none;
			margin-right:0;
		}
	}
	#sell{
		font-size: 18rpx;
		color: #606060;
	}
</style>
