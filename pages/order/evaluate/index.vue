<template>
	<view class="content">
		<view class="goods">
			<view class="goods-dian">
				<image src="../../../static/user/dian.png"></image>
				<view>多彩結好</view>
			</view>
			<view class="goods-img">
				<view class="img">
					<image src="../../../static/banner.png" mode="aspectFill"></image>
				</view>
				<view class="goods-name">
					<view class="name">
						<view class="na">多彩好結</view>
						<view>¥1</view>
					</view>
					<view class="goods-mun">x1</view>
				</view>
			</view>
		</view>
		<view class="card">
			<u-cell-item  title="整单评价" :arrow="false"></u-cell-item>
			<u-cell-item  title="评分" :arrow="false" class="u-cell-item">
				<view style="float: left;margin-left: 60rpx;">
					<u-rate :count="count" v-model="value" size="40"></u-rate>
				</view>
			</u-cell-item>
			<u-cell-item  title="晒图" :arrow="false" class="u-cell-item">
				<view style="float: left;margin-left: 60rpx;">
					<u-upload ref="uUpload" @change="submit()" :action="action"></u-upload>
				</view>
			</u-cell-item>
			<!-- <u-cell-item  title="评价" :arrow="false">
				<view class="text">
					<textarea placeholder="说点什么" auto-height="true" placeholder-style="font-size: 30rpx;"></textarea>
				</view>
			</u-cell-item> -->
			<u-field  label="评价" placeholder="说点什么" type="textarea" ></u-field>
		</view>
		<view class="btn">提交评论</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				count: 5,
				value: '',
				action: 'http://www.example.com/upload',
				filesArr: [],
			}
		},
		onLoad() {

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
		}
	}
</script>

<style lang="scss">
	page{
		background: #F2F5FA;
	}
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	.goods{
		background: #FFFFFF;
		width: 94%;
		margin-top: 20rpx;
		border-radius: 15rpx;
		padding: 20rpx;
		padding-bottom: 30rpx;
	}
	.goods-dian{
		display: flex;
		flex-direction: row;
		height: 80rpx;
		align-items: center;
		border-bottom: 1rpx solid #ddd;
	}
	.goods-dian>image{
		width: 55rpx;
		height: 55rpx;
	}
	.goods-dian>view{
		margin-left: 10rpx;
		font-size: 30rpx;
	}
	.goods-img{
		display: flex;
		flex-direction: row;
		margin-top: 20rpx;
	}
	.img{
		width: 200rpx;
		height: 200rpx;
	}
	.img>image{
		width: 100%;
		height: 100%;
	}
	.goods-name{
		// width:calc(100% - 200px);
		width:450rpx;
		height: 200rpx;
		display: flex;
		flex-direction: column;
		margin-left: 10rpx;
	}
	.name{
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		font-size: 30rpx;
	}
	.na{
		width: 400rpx;
		overflow: hidden;
	}
	.goods-mun{
		text-align: right;
		font-size: 30rpx;
		margin-top: 5rpx;
	}
	.card{
		width: 94%;
		background: #FFFFFF;
		margin-top: 30rpx;
		border-radius: 20rpx;
		padding: 0rpx 20rpx;
	}
	.text{
		display: flex;
		flex-direction: column;
		min-height: 50rpx;
		width: 550rpx;
		text-align: left;
		float: left;
		margin-left: 60rpx;
	}
	.btn{
		position: fixed;
		bottom: 0rpx;
		left: 0rpx;
		z-index: 2;
		width: 100%;
		height: 80rpx;
		line-height: 80rpx;
		text-align: center;
		background: #ff5500;
		color: #FFFFFF;
	 }
</style>
