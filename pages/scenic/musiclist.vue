<template>
	<view class="content">
		<view class="list-item" v-for="item in musiclist">
			<image src="../../static/scenic/music2.png" mode="" class="left icon1"></image>
			<view class="musicinfo left">
				<view class="topname">
					{{item.name}}-{{item.geshou}}
				</view>
				<view class="size">
					大小:{{item.size}}MB
				</view>
			</view>
			<image src="../../static/scenic/xiazai.png" mode="" class="right xiazai"></image>
			<image src="../../static/scenic/iscol.png" mode="" class="right iscol" v-if="item.iscol==1"></image>
			<image src="../../static/food/col.png" mode="" v-else-if="item.iscol==0" class="col right"></image>
			<image src="../../static/scenic/play.png" mode="" class="right play"></image>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				musiclist:[
					{
						name:'晴天',
						geshou:'周杰伦',
						iscol:0,
						size:4.25
					},
					{
						name:'曹操',
						geshou:'林俊杰',
						iscol:0,
						size:4.5
					},
					{
						name:'稻香',
						geshou:'周杰伦',
						iscol:0,
						size:4.8
					}
				]
			};
		}
	}
</script>

<style lang="scss">
	page{
		background: #f1f1f1;
	}
	.list-item{
		width: 686rpx;
		margin: auto;
		height: 86rpx;
		border-bottom: 1px solid #D9D9D9;
	}
	.icon1{
		width: 40rpx;
		height: 40rpx;
		margin-top: 25rpx;
	}
	.musicinfo{
		width: 300rpx;
		text-overflow: ellipsis;
		overflow: hidden;
		white-space: nowrap;
		height: 100%;
		margin-left: 7px;
	}
	.topname{
		margin-top: 5px;
	}
	.size{
		// margin-top: 5px;
		font-size: 10px;
		color: #9B9B9B;
	}
	.xiazai{
		width: 28rpx;
		height: 25rpx;
		margin-top: 30rpx;
	}
	.iscol,.col{
		width: 32rpx;
		height: 30rpx;
		margin-top: 30rpx;
		margin-right: 28rpx;
	}
	.play{
		width: 32rpx;
		height: 31rpx;
		margin-top: 30rpx;
		margin-right: 28rpx;
	}
</style>
