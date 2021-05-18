<template>
	<view class="nav">
		<view @click="change(0)" class="nav-ul"><text :class="[btnnum=='0'?'active':'text']">未使用</text></view>
		<view @click="change(1)" class="nav-ul"><text :class="[btnnum==1?'active':'text']">已使用</text></view>
		<view @click="change(2)" class="nav-ul"><text :class="[btnnum==2?'active':'text']">已过期</text></view>
	</view>
	<!-- <view class="list"></view> -->
</template>

<script>
	export default {
		data() {
			return {
				btnnum: '0'
			}
		},
		onLoad() {

		},
		
		methods: {
			change(e) {
				this.btnnum = e
				// console.log(this.btnnum)
			},
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
		display: flex;
		top: 0;
		left: 0;
		height: 100rpx;
		width: 100%;
		z-index: 99999;
		background: #ffffff;
	}
	.nav-ul{
		width: 33.3%;
		height: 100rpx;
		text-align: center;
	}
	.nav-ul>.text{
		display: inline-block;
		color: #676767;
		height: 100rpx;
		font-size: 40rpx;
		font-weight: bold;
		line-height: 100rpx;
	}
	.active{
		display: inline-block;
		font-size: 40rpx;
		height: 96rpx;
		line-height: 98rpx;
		color: #000000;
		font-weight: bold;
		border-bottom: 4rpx solid #32B134;
	}
	/* 优惠券列表 */
	.list{
		background: #FFFFFF;
		margin-top: 150rpx;
		width: 96%;
		height: 200rpx;
	}	
</style>
