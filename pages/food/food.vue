<template>
	<view class="content">
		<view class="list_item" v-for="item in list" @tap="goinfo(item.text)">
			
			<image :src="item.src" mode="" class="topimg"></image>
			<view class="text">
				{{item.text}}
			</view>
			<!-- <image src="../../images/bbb.png" mode=""></image> -->
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list:[
					{
						src:'https://cdn.uviewui.com/uview/swiper/1.jpg',
						text:"江口米豆腐"
					},
					{
						src:'https://cdn.uviewui.com/uview/swiper/2.jpg',
						text:"锅巴粉"
					}
				]
			}
		},
		methods: {
			goinfo(text){
				uni.navigateTo({
					url:"./foodinfo?name="+text
				})
			}
		}
	}
</script>

<style lang="scss">
	page{
		background-color: #F5F3F3;
	}
	.list_item{
		width: 726rpx;
		height: 405rpx;
		margin-top: 16rpx;
		background: #FFFFFF;
		border-radius: 6px;
	}
	.topimg{
		width: 726rpx;
		height: 342rpx;
		border-radius: 0;
	}
	.text{
		margin-left: 20rpx;
		color: #000000;
		font-weight: 600;
	}
</style>
