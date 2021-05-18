<template>
	<view class="content">
		<u-navbar :border-bottom="false">
			<view class="slot-wrap" slot="right" @tap="gorelease()">
				发布
			</view>
		</u-navbar>
		<u-upload ref="uUpload" @change="submit()" :action="action"></u-upload>
		<view class="textarea">
			<u-input v-model="value" type="textarea" :height="280" placeholder="说点什么吧～～"/>
		</view>
		<view class="loction">
			<image src="../../static/dongtai/dizhi1.png" mode="" class="left loc"></image>
			<view class="dizhi left">
				{{loction}}
			</view>
			<image src="../../static/dongtai/jianyou.png" mode="" class="right jian"></image>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				action: 'http://www.example.com/upload',
				value: '',
				filesArr: [],
				loction:"贵阳观山湖区德福中心"
			}
		},
		methods: {
			submit() {
				let files = [];
				// 通过filter，筛选出上传进度为100的文件(因为某些上传失败的文件，进度值不为100，这个是可选的操作)
				files = this.$refs.uUpload.lists.filter(val => {
					return val.progress == 100;
				})
				// 如果您不需要进行太多的处理，直接如下即可
				// files = this.$refs.uUpload.lists;
				console.log(files)
			},
			gorelease(){
				// 上传完毕后跳转到动态首页
				uni.switchTab({
					url:"../dongtai/index"
				})
			}
		}
	}
</script>

<style lang="scss">
	.content{
		padding: 0rpx 40rpx;
	}
	.slot-wrap {
		float: right;
		width: 50px;
		height: 20px;
		background: #32B134;
		text-align: center;
		color: #FFFFFF;
		line-height: 20px;
		border-radius: 9px;
		margin-right: 17px;
		font-size: 15px;
	}
	.textarea{
		width: 100%;
		border-bottom: 1px solid #D9D9D9;
	}
	.loction{
		width: 100%;
		margin-top: 50rpx;
	}
	.loc{
		width: 30rpx;
		height: 37rpx;
	}
	.jian{
		width: 14rpx;
		height: 25rpx;
		margin-right: 20rpx;
	}
	.dizhi{
		margin-left: 15rpx;
	}
</style>
