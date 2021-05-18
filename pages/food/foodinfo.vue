<template>
	<view class="content">
		<image :src="imgurl" mode="" class="img"></image>
		<view class="btns">
			<view class="name left">
				{{name}}
			</view>
			<view class="right btnbox">
				<!-- 需要判断是否已经收藏 -->
				<image src="../../static/food/share.png" mode="" class="topimg"></image>
				<view class="bottomtxt">
					分享
				</view>
			</view>
			<view class="right btnbox">
				<image src="../../static/food/col.png" mode="" class="topimg"></image>
				<view class="bottomtxt">
					收藏
				</view>
			</view>
		</view>
		<view class="textarea">
			{{text}}
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				imgurl:"https://cdn.uviewui.com/uview/swiper/2.jpg",
				name:'',
				text:'江口米豆腐嫩黄鲜亮，晶莹剔透，可切成片、条、块或制成虾仁米豆腐，配以江口特制的油辣椒、醋辣椒、佐料，酸香麻辣，滑软可口，凉吃热煮均可。'
			}
		},
		onLoad(option) {
			this.name=option.name
			uni.setNavigationBarTitle({
				title:option.name
			})
		},
		methods: {
			
		}
	}
</script>

<style lang="scss">
	.img{
		width: 750rpx;
		height: 525rpx;
	}
	.btns{
		width: 670rpx;
		border-bottom: 1px solid #e5e5e5;
		height: 106rpx;
	}
	.name{
		line-height: 106rpx;
		font-weight: 600;
	}
	.topimg{
		width: 30rpx;
		height: 30rpx;
	}
	.btnbox{
		margin-top: 25rpx;
		width: 45rpx;
		text-align: center;
		font-size: 12px;
	}
	.btnbox:last-of-type{
		margin-right: 69rpx;
	}
	.textarea{
		width: 670rpx;
		height: auto;
		margin-top: 27rpx;
	}
</style>
