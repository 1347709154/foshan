<template>
	<view class="content">
		<view class="list-item" v-for="item in menulist" :style="{backgroundImage: 'url('+item.imgurl+')'}" @tap="golink(item.links)">
			<view class="centerbox">
				{{item.title}}
			</view>
		</view>
		<!--  拼接渐变背景 -->
		<!-- <view class="list-item" v-for="item in menulist" :style="{backgroundImage:'linear-gradient('+color[0]+','+color[1]+')'}">
			fss
		</view> -->
	</view>
</template>

<script>
	export default {
		data() {
			return {
				menulist: [{
						title: '景区简介',
						imgurl: 'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fbig5.www.gov.cn%2Fgate%2Fbig5%2Fwww.gov.cn%2Fxinwen%2F2020-05%2F21%2F5513506%2Fimages%2F760f3df93b5f4582be1a0549a4478835.JPG&refer=http%3A%2F%2Fbig5.www.gov.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1623916316&t=2a315d874e66eecc25a742c2da9d714f',
						links: './scenicarea'
					},
					{
						title: '旅游攻略',
						imgurl: 'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg.article.pchome.net%2F00%2F33%2F22%2F95%2Fpic_lib%2Fs960x639%2F1920CHINA_2020s960x639.jpg&refer=http%3A%2F%2Fimg.article.pchome.net&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1623916725&t=c65b0f9354327691518c42d1475ac84b',
						links: './strategy'
					},
					{
						title: '景点介绍',
						imgurl: 'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg2.niutuku.com%2Fdesk%2F1208%2F0856%2Fbizhi-0856-17290.jpg&refer=http%3A%2F%2Fimg2.niutuku.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1623916725&t=00eab6ba43013ed976336dafa3aa558d',
						links: './sceniclist'
					},
					{
						title: '导赏手册',
						imgurl: 'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Finews.gtimg.com%2Fnewsapp_match%2F0%2F10745474838%2F0.jpg&refer=http%3A%2F%2Finews.gtimg.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1623916725&t=043b466564f9a4a1e9100624479ed2c3',
						links: './travelpath'
					},
					{
						title: '游客须知',
						imgurl: 'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fi.shedejie.com%2Fmmbiz_jpg%2FlgQWDzmC67nrPDL8oG65RONialrrmuWxdfRLzEGwFRUqJEy6obX1mngV3JuG8CtYHwiafdTlSTM9H9OGTThX85dw%2F0.jpeg%3F&refer=http%3A%2F%2Fi.shedejie.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1623916946&t=fe3a6b45020680faa9e89fd677299372',
						links: './touristnotice'
					},
				],
			};
		},
		methods:{
			golink(url){
				uni.navigateTo({
					url:url
				})
			}
		}
	}
</script>

<style lang="scss">
	.list-item {
		width: 721rpx;
		height: 250rpx;
		border-radius: 15rpx;
		margin-top: 13rpx;
		background-size: cover;
		background-repeat: no-repeat;
		position: relative;
	}

	.centerbox {
		width: 358rpx;
		height: 61rpx;
		// background: rgba(0, 0, 0, 0.32);
		// border: 1px solid #FFFFFF;
		border-bottom: 1px solid #FFFFFF;
		border-top: 1px solid #FFFFFF;
		box-sizing: border-box;
		border-image: -webkit-linear-gradient(90deg, rgba(255, 255, 255, 0.00) 0%, #FFFFFF 20%, rgba(255, 255, 255, 0.00) 99%) 2 2 2 2;
		border-image: -moz-linear-gradient(90deg, rgba(255, 255, 255, 0.00) 0%, #FFFFFF 20%, rgba(255, 255, 255, 0.00) 99%) 2 2 2 2;
		border-image: linear-gradient(90deg, rgba(255, 255, 255, 0.00) 0%, #FFFFFF 20%, rgba(255, 255, 255, 0.00) 99%) 2 2 2 2;
		background: radial-gradient(rgba(0, 0, 0, 0.32), rgba(0, 0, 0, 0.1));
		border-radius: 9rpx;
		position: absolute;
		left: 50%;
		top: 50%;
		transform: translate(-50%, -50%);
		text-align: center;
		line-height: 61rpx;
		color: #FFFFFF;
		font-size: 36rpx;
	}
</style>
