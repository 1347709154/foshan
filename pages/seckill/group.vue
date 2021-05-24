<template>
	<view class="content">
		<view class="list" v-for="item in goodslist">
			<view class="goodsimg">
				<u-swiper :list="item.imglist" mode="none" border-radius="0" height="445" width="726"></u-swiper>
			</view>
			<p class="title">{{item.name}}</p>
			<view class="progess">
				<view class="left jindu">
					<u-line-progress active-color="#FD5052" inactive-color="#F2ABA9" :percent="(item.sellnum/item.totalnum*100)"
					 height="23" :show-percent="false"></u-line-progress>
				</view>
				<view class="left sell">
					已团购{{item.sellnum}}件
				</view>
			</view>
			<view class="botombox">
				<view class="left price">
					<p>团购价<span class="fu">¥</span><span class="jia">{{item.miaoprice}}</span></p>
				</view>
				<view class="right btns" @tap="goinfo">
					去团购	>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				goodslist: [{
						name: '精品糕点',
						imglist: [
							'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fb-ssl.duitang.com%2Fuploads%2Fitem%2F201503%2F07%2F20150307230620_e8s38.thumb.700_0.jpeg&refer=http%3A%2F%2Fb-ssl.duitang.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1624091205&t=c6246693ab35f1a6c800196c6733a713',
							'https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=2361007573,1113070349&fm=224&gp=0.jpg'
						],
						totalnum: 190,
						sellnum: 100,
						miaoprice: 13.00,

					},
					{
						name: '黄焖鸡米饭',
						imglist: [
							'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimages.3158.cn%2Fdata%2Fattachment%2Ftougao%2Farticle%2F2017%2F11%2F23%2F19c8b7686d4052ef06c11921037d10b1.jpg&refer=http%3A%2F%2Fimages.3158.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1624091582&t=e1debceda2f141781e3eae6e1c05ee06',
							'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimage.zhms.cn%2F2018050811113418895.jpg%3Fx-oss-process%3Dimage%2Fformat%2Cjpg%2Finterlace%2C1%2Fwatermark%2Cimage_RGVmYXVsdC9iLnBuZw%3D%3D%2Ct_35%2Cg_se%2Cx_10%2Cy_10&refer=http%3A%2F%2Fimage.zhms.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1624091582&t=5b159ccb0758bb945f367dd54030a06b'
						],
						totalnum: 200,
						sellnum: 40,
						miaoprice: 7.00,

					}
				]
			};
		},
		methods:{
			goinfo(){
				uni.navigateTo({
					url:"/pages/seckill/group-details"
				})
			}
		}
	}
</script>

<style lang="scss">
	page{
		background: #f3f3f3;
	}
	.list {
		width: 726rpx;
		height: 662rpx;
		background: #FFFFFF;
		border-radius: 19rpx;
		margin: auto;
		margin-top: 17rpx;
		overflow: hidden;
	}
	.progess{
		margin-top: 20rpx;
		height: 40rpx;
	}
	.goodsimg{
		width: 726rpx;
		height: 445rpx;
	}
	.title{
		font-size: 36rpx;
		color: #010101;
		padding-left: 35rpx;
		margin-top: 20rpx;
	}
	.jindu{
		width: 262rpx;
		margin-left: 35rpx;
	}
	.sell{
		margin-left: 15rpx;
		color: #868686;
		font-size: 24rpx;
	}
	.botombox{
		height: 63rpx;
	}
	.btns{
		width: 164rpx;
		height: 63rpx;
		line-height: 63rpx;
		text-align: center;
		background: #EF1E22;
		border-radius: 4rpx;
		color: #FFFFFF;
		margin-right: 30rpx;
	}
	.price{
		color: #DF2911;
		padding-left: 35rpx;
		font-size: 26rpx;
		line-height:83rpx;
	}
	.fu{
		margin-left: 10rpx;
	}
	.jia{
		margin-left: 10rpx;
		font-size: 36rpx;
	}
</style>
