<template>
	<view class="content">
		<!-- <image class="logo" src="/static/logo.png"></image> -->
		<u-navbar :is-back="false" title="动态" :border-bottom="false">
			<view class="slot-wrap" slot="right" @tap="gorelease()">
				发布
			</view>
		</u-navbar>
		<view class="end-title">
			<view>
				<view v-for="(item,index) in items" :key="index" :class="{btna:count == index}" @tap="change(index)" class="card">
					{{item}}
				</view>
			</view>

		</view>
		<view class="end-cont" :class="{dis:btnnum == 0}">
			<view class="msglist" v-for="(items,index) in msglist">
				<view class="avt">
					<view class="left tou">
						<u-avatar :size="73" :src="items.src"></u-avatar>
					</view>
					<view class="left text">
						{{items.nickname}}
					</view>
				</view>
				<view class="swiper">
					<u-swiper :list="items.list" :height="674" :width="750" mode="number" indicator-pos="bottomRight"></u-swiper>
				</view>
				<view class="textbox">
					<view class="loction">
						<view class="left icon">
							<image src="../../static/dongtai/dizhi.png" mode=""></image>
						</view>
						<view class="left locname">
							{{items.address}}
						</view>
					</view>
					<view class="title">
						{{items.title}}
					</view>
					<view class="flexoarea">
						<!-- 这里要判断用户是否已经点赞或收藏 -->
						<view class="caozuolist">
							<image src="../../static/dongtai/xin1.png" mode="" class="left"></image>
							<view class="count left">
								{{items.count}}
							</view>
						</view>
						<view class="caozuolist">
							<image src="../../static/dongtai/xx.png" mode=""></image>
						</view>
						<view class="caozuolist">
							<image src="../../static/dongtai/bi.png" mode=""></image>
						</view>
						<view class="caozuolist">
							<image src="../../static/dongtai/zhuangfa.png" mode=""></image>
						</view>
					</view>
					<!-- 需要判断是否已经有评论 -->
					<view class="evlbox">
						<u-input :border="true" :height="46" placeholder="发表评论......" />
					</view>
				</view>
			</view>

		</view>
		<view class="end-cont" :class="{dis:btnnum == 1}">
			　　<view class="msglist" v-for="(items,index) in msglist2">
				<view class="avt">
					<view class="left tou">
						<u-avatar :size="73" :src="items.src"></u-avatar>
					</view>
					<view class="left text">
						{{items.nickname}}
					</view>
				</view>
				<view class="swiper">
					<u-swiper :list="items.list" :height="674" :width="750" mode="number" indicator-pos="bottomRight"></u-swiper>
				</view>
				<view class="textbox">
					<view class="loction">
						<view class="left icon">
							<image src="../../static/dongtai/dizhi.png" mode=""></image>
						</view>
						<view class="left locname">
							{{items.address}}
						</view>
					</view>
					<view class="title">
						{{items.title}}
					</view>
					<view class="flexoarea">
						<!-- 这里要判断用户是否已经点赞或收藏 -->
						<view class="caozuolist">
							<image src="../../static/dongtai/xin1.png" mode="" class="left"></image>
							<view class="count left">
								{{items.count}}
							</view>
						</view>
						<view class="caozuolist">
							<image src="../../static/dongtai/xx.png" mode=""></image>
						</view>
						<view class="caozuolist">
							<image src="../../static/dongtai/bi.png" mode=""></image>
						</view>
						<view class="caozuolist">
							<image src="../../static/dongtai/zhuangfa.png" mode=""></image>
						</view>
					</view>
					<!-- 需要判断是否已经有评论 -->
					<view class="evlbox">
						<u-input :border="true" :height="46" placeholder="发表评论......" />
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
				title: 'Hello',
				btnnum: 0,
				items: ["游客动态", "志愿者动态"],
				count: "",
				msglist: [{
						nickname: "测试测试测试",
						src: "https://ewr1.vultrobjects.com/imgspice2/000/004/888/353_1a8_8d1.jpg",
						list: [{
								image: 'https://cdn.uviewui.com/uview/swiper/1.jpg'
							},
							{
								image: 'https://cdn.uviewui.com/uview/swiper/2.jpg'
							},
							{
								image: 'https://cdn.uviewui.com/uview/swiper/3.jpg'
							}
						],
						address: "安徽黄山",
						title: "五一出游去山间看看吧 不会后悔的，没有人挤人，没有车挤车 找一家山间的美食民宿",
						count: 2000
					},
					{
						nickname: "测试测试测试",
						src: "https://ewr1.vultrobjects.com/imgspice2/000/004/888/353_1a8_8d1.jpg",
						list: [{
								image: 'https://cdn.uviewui.com/uview/swiper/1.jpg'
							},
							{
								image: 'https://cdn.uviewui.com/uview/swiper/2.jpg'
							},
							{
								image: 'https://cdn.uviewui.com/uview/swiper/3.jpg'
							}
						],
						address: "重庆九龙坡",
						title: "五一出游去山间看看吧 不会后悔的，没有人挤人，没有车挤车 找一家山间的美食民宿",
						count: 999,

					},
				],
				msglist2: [{
						nickname: "王二",
						src: "https://ewr1.vultrobjects.com/imgspice2/000/004/888/353_1a8_8d1.jpg",
						list: [{
								image: 'https://cdn.uviewui.com/uview/swiper/1.jpg'
							},
							{
								image: 'https://cdn.uviewui.com/uview/swiper/2.jpg'
							},
							{
								image: 'https://cdn.uviewui.com/uview/swiper/3.jpg'
							}
						],
						address: "九寨沟",
						title: "五一出游去山间看看吧 不会后悔的，没有人挤人，没有车挤车 找一家山间的美食民宿",
						count: 2000
					},
					{
						nickname: "李四",
						src: "https://ewr1.vultrobjects.com/imgspice2/000/004/888/353_1a8_8d1.jpg",
						list: [{
								image: 'https://cdn.uviewui.com/uview/swiper/1.jpg'
							},
							{
								image: 'https://cdn.uviewui.com/uview/swiper/2.jpg'
							},
							{
								image: 'https://cdn.uviewui.com/uview/swiper/3.jpg'
							}
						],
						address: "九寨沟",
						title: "五一出游去山间看看吧 不会后悔的，没有人挤人，没有车挤车 找一家山间的美食民宿",
						count: 999,
				
					},
				]

			}
		},
		onLoad() {

		},
		methods: {
			change(e) {
				this.count = e
				this.btnnum = e
				console.log(this.count)
			},
			gorelease(){
				uni.navigateTo({
					url:"../release/release"
				})
				console.log(111)
			}
		}
	}
</script>

<style lang="scss">
	page {
		background-color: #F5F3F3;
	}

	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}

	.u-swiper-wrap {
		width: 750rpx;
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

	/* 将三个内容view的display设置为none(隐藏) */
	.end-title {
		height: 68rpx;
		display: flex;
		width: 100%;
		color: #1A1B1B;
		background-color: #FFFFFF;
		position: fixed;
		top: 44px;
		z-index: 999;
	}

	.end-title view {
		flex-grow: 1;
		text-align: center;
	}

	.end-cont {
		display: none;
		width: 100%;
		margin-top: 35px;
	}

	.btna {
		color: #32B134;
	}

	.dis {
		display: block;
	}

	.card {
		width: 375rpx;
		box-sizing: border-box;
		margin: 9px 0px;
	}

	.card:first-of-type {

		border-right: #EEEEEE 1px solid;
		float: left;
	}

	.card:last-of-type {
		float: right;
	}

	.avt {
		height: 73rpx;
		margin-top: 50rpx;
		line-height: 73rpx;
	}

	.tou {
		margin-left: 25rpx;
	}

	.text {
		margin-left: 16rpx;
	}

	.swiper {
		width: 100%;
		height: 672rpx;
		margin-top: 15px;
	}

	.msglist {
		overflow: hidden;
		margin-top: 8px;
		background: #FFFFFF;
	}

	.textbox {
		min-height: 415rpx;
		overflow: hidden;
	}

	.loction {
		// height: 40rpx;
		// line-height: 40rpx;
		overflow: hidden;
	}

	.icon {
		width: 30rpx;
		height: 40rpx;

		image {
			width: 30rpx;
			height: 40rpx;
		}

		margin-top: 19rpx;
		margin-left: 25rpx;
	}

	.locname {
		margin-top: 10px;
		margin-left: 15rpx;
		color: #171414;
	}

	.title {
		padding: 0rpx 25rpx;
		font-size: 13px;
		color: #5A5A5A;
		margin-top: 15px;
	}

	.flexoarea {
		overflow: hidden;
		display: flex;
		height: 45rpx;
		padding: 0px 25rpx;
		line-height: 53rpx;
		margin-top: 15px;

		image {
			width: 40rpx;
			height: 35rpx;
			margin-top: 5px;
			// display: ;
		}
	}

	.caozuolist {
		width: 100rpx;
	}

	.caozuolist:first-of-type {
		width: 130rpx;
	}

	.count {
		margin-left: 2px;
	}

	.evlbox {
		width: 706rpx;
		height: 46rpx;
		margin: auto;
		background: #F5F5F5;
		margin-top: 30rpx;
	}

	.uni-input-placeholder {
		color: #848383;
		font-size: 12px;
	}
</style>
