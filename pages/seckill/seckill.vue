<template>
	<view class="content">
		<view class="bgbox">
			<image src="../../static/scenic/pingtuan.png" mode=""></image>
		</view>
		<view class="listitem">
			<view class="end-title">
				<view>
					<view v-for="(item,index) in begintime" :class="{btna:count == index}" @tap="change(index)" class="card">
						<view class="titlebox">
							{{item |dateFormat}}
							<span v-if="endtime[index]>nowtime && nowtime>=item">开抢中</span>
							<span v-else-if="nowtime < item">
								即将开抢
							</span>
							<span v-else-if="nowtime > item">已结束</span>
						</view>
						<view class="line">

						</view>
					</view>
				</view>

			</view>
			<view class="end-cont" :class="{dis:btnnum == 0}">
				<view class="goods" v-for="item in qianggoodslist">
					<view class="goodsimg">
						<u-swiper :list="item.imglist" mode="none" border-radius="0" height="352" width="702"></u-swiper>
					</view>
					<p class="goodsname">{{item.name}}</p>
					<view class="jindubox" v-if="nowtime>=item.begintime && item.endtime>nowtime">
						<view class="left jindu">
							<u-line-progress active-color="#FD5052" inactive-color="#F2ABA9" :percent="(item.sellnum/item.totalnum*100)"
							 height="12" :show-percent="false"></u-line-progress>
						</view>
						<view class="right status">
							抢购中
						</view>
					</view>
					<view class="jindubox" v-else-if="nowtime>item.endtime">
						<!-- <view class="left jindu">
							<u-line-progress active-color="#FD5052" inactive-color="#F2ABA9" :percent="(item.sellnum/item.totalnum*100)" height="12" :show-percent="false"></u-line-progress>
						</view> -->
						<view class="right status">
							已结束
						</view>
					</view>
					<view class="jindubox" v-else-if="nowtime<item.begintime">
						<p class="nums">限量{{item.totalnum}}件|{{item.begintime |dateFormat}}</p>
					</view>
					<view class="bottombox" v-if="nowtime>=item.begintime && item.endtime>nowtime">
						<view class="left">
							<p><span class="miao">秒杀价 ¥</span><span class="miaop">{{item.miaoprice}}</span></p>
							<p class="notice">最低价，即将恢复原价</p>
						</view>
						<view class="right btns" @tap.stop="goosinfo">
							立即购买
						</view>
					</view>
					<view class="bottombox" v-else-if="nowtime<item.begintime">
						<view class="left">
							<p class="jjkq"><span class="miao">秒杀价 ¥</span><span class="miaop">{{item.miaoprice}}</span></p>
						</view>
						<view class="right btns jjkqbtn" v-if="nowtime<item.begintime">
							即将开抢
						</view>
					</view>
					<view class="bottombox" v-else-if="nowtime>item.endtime">
						<view class="left">
							<!-- <p><span class="miao">秒杀价 ¥</span><span class="miaop">{{item.miaoprice}}</span></p> -->
							<p class="notice">抢购结束，已恢复原价</p>
						</view>
						<view class="right btns">
							抢购结束
						</view>
					</view>
				</view>
			</view>
			<view class="end-cont" :class="{dis:btnnum == 1}">
				<view class="goods" v-for="item in qianggoodslist2">
					<view class="goodsimg">
						<u-swiper :list="item.imglist" mode="none" border-radius="0" height="352" width="702"></u-swiper>
					</view>
					<p class="goodsname">{{item.name}}</p>
					<view class="jindubox" v-if="nowtime>=item.begintime && item.endtime>nowtime">
						<view class="left jindu">
							<u-line-progress active-color="#FD5052" inactive-color="#F2ABA9" :percent="(item.sellnum/item.totalnum*100)"
							 height="12" :show-percent="false"></u-line-progress>
						</view>
						<view class="right status">
							抢购中
						</view>
					</view>
					<view class="jindubox" v-else-if="nowtime>item.endtime">
						<!-- <view class="left jindu">
							<u-line-progress active-color="#FD5052" inactive-color="#F2ABA9" :percent="(item.sellnum/item.totalnum*100)" height="12" :show-percent="false"></u-line-progress>
						</view> -->
						<view class="right status">
							已结束
						</view>
					</view>
					<view class="jindubox" v-else-if="nowtime<item.begintime">
						<p class="nums">限量{{item.totalnum}}件|{{item.begintime |dateFormat}}</p>
					</view>
					<view class="bottombox" v-if="nowtime>=item.begintime && item.endtime>nowtime">
						<view class="left">
							<p><span class="miao">秒杀价 ¥</span><span class="miaop">{{item.miaoprice}}</span></p>
							<p class="notice">最低价，即将恢复原价</p>
						</view>
						<view class="right btns" @tap.stop="goosinfo">
							立即购买
						</view>
					</view>
					<view class="bottombox" v-else-if="nowtime<item.begintime">
						<view class="left">
							<p class="jjkq"><span class="miao">秒杀价 ¥</span><span class="miaop">{{item.miaoprice}}</span></p>
						</view>
						<view class="right btns jjkqbtn" v-if="nowtime<item.begintime">
							即将开抢
						</view>
					</view>
					<view class="bottombox" v-else-if="nowtime>item.endtime">
						<view class="left">
							<!-- <p><span class="miao">秒杀价 ¥</span><span class="miaop">{{item.miaoprice}}</span></p> -->
							<p class="notice">抢购结束，已恢复原价</p>
						</view>
						<view class="right btns">
							抢购结束
						</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import {
		dateFormatWithFmt
	} from "../../common/date.js"
	export default {
		data() {
			return {
				btnnum: 0,
				count: '',
				begintime: ['1621503537000', '1638523800000'],
				endtime: ['1639993200000', '1639993200000'],
				nowtime: '',
				qianggoodslist: [{
						name: '铜仁特产黄水粑4只装',
						imglist: [
							'https://gimg2.baidu.com/image_search/src=http%3A%2F%2F5b0988e595225.cdn.sohucs.com%2Fimages%2F20180725%2F0f8b34008d444d75abddf1361f7621a4.jpeg&refer=http%3A%2F%2F5b0988e595225.cdn.sohucs.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1624089386&t=b87326947110f4b1e23f3cb0cafe21fc',
							'https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=3757765567,451971902&fm=26&gp=0.jpg'
						],
						totalnum: 100,
						sellnum: 40,
						begintime: '1621503537000',
						endtime: '1639993200000',
						miaoprice: 5.20,

					},
					{
						name: '美味蛋糕',
						imglist: [
							'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fcp1.douguo.com%2Fupload%2Fcaiku%2Fb%2F6%2Fd%2Fyuan_b62036b32d49b067d761d8a81bd64ccd.jpeg&refer=http%3A%2F%2Fcp1.douguo.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1624091205&t=db2ebde4cc51cf9616d9b068fd2376bd',
							'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fb-ssl.duitang.com%2Fuploads%2Fitem%2F201803%2F09%2F20180309174757_kRPcN.jpeg&refer=http%3A%2F%2Fb-ssl.duitang.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1624091205&t=7120a73322cbb3d12d055f3078467b9e'
						],
						totalnum: 180,
						sellnum: 40,
						begintime: '1621503537000',
						endtime: '1639993200000',
						miaoprice: 5.50,

					}
				],
				qianggoodslist2: [{
						name: '精品糕点',
						imglist: [
							'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fb-ssl.duitang.com%2Fuploads%2Fitem%2F201503%2F07%2F20150307230620_e8s38.thumb.700_0.jpeg&refer=http%3A%2F%2Fb-ssl.duitang.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1624091205&t=c6246693ab35f1a6c800196c6733a713',
							'https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=2361007573,1113070349&fm=224&gp=0.jpg'
						],
						totalnum: 190,
						sellnum: 100,
						begintime: '1638523800000',
						endtime: '1639993200000',
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
						begintime: '1638523800000',
						endtime: '1639993200000',
						miaoprice: 7.00,

					}
				]
			};
		},
		methods: {
			change(e) {
				this.count = e
				this.btnnum = e
				console.log(this.count)
			},
			gettime() {
				var tempDate = new Date().getTime(); // "Mon Sep 30 2019 20:51:28 GMT+0800 (中国标准时间)"
				this.nowtime = tempDate.toString()
				console.log(tempDate)
			},
			goosinfo(){
				console.log(111)
			}
		},
		filters: {
			dateFormat(date) {
				console.log(date)
				var datenow = date

				function set_time(str) {
					var n = parseInt(datenow);
					var D = new Date(n);
					var hours = D.getHours(); //小时(0-23)
					hours = hours < 10 ? ('0' + hours) : hours;

					var minutes = D.getMinutes(); //分钟(0-59)
					minutes = minutes < 10 ? ('0' + minutes) : minutes;

					// var seconds = D.getSeconds();//秒(0-59)
					// seconds = seconds<10?('0'+seconds):seconds;
					// var week = D.getDay();//周几(0-6),0为周日
					// var weekArr = ['周日','周一','周二','周三','周四','周五','周六'];

					var now_time = hours + ':' + minutes;
					return now_time;
				}
				var datetime = set_time(date)
				// var date = timestampToTime(date)
				return datetime

			},
		},
		mounted() {
			this.gettime()
		}
	}
</script>

<style lang="scss">
	.bgbox {
		width: 750rpx;
		text-align: center;
		height: 389rpx;
		background: linear-gradient(180deg, #D73729, #F5826D);

		image {
			width: 726rpx;
			height: 311rpx;
		}
	}

	.listitem {
		width: 100%;
		min-height: 400rpx;
		height: auto;
		border-radius: 40rpx 40rpx 0 0;
		background: white;
		margin-top: -60rpx;
	}

	.end-title {
		height: 87rpx;
		display: flex;
		width: 698rpx;
		color: #1A1B1B;
		// padding: 0 25rpx;
		background-color: #FFFFFF;
		// position: fixed;
		// top: 44px;
		border-radius: 22px 22px 0 0;
		z-index: 999;
	}

	.end-title view {
		flex-grow: 1;
		text-align: center;
	}

	.btna {
		color: #EF1E22;

		.line {
			width: 163rpx;
			height: 4rpx;
			background: #FD5052;
			margin: auto;
		}
	}

	.end-cont {
		display: none;
		width: 100%;
		// margin-top: 35px;
	}

	.dis {
		display: block;
	}

	.card {
		// height: 40rpx;
		width: calc(698rpx/2);
		box-sizing: border-box;
		// margin: 9px 0px;
		line-height: 87rpx;
		// margin-top: 20rpx;
		// text-decoration: underline;
	}

	.titlebox {
		height: 70rpx;
	}

	.card:first-of-type {

		// border-right: #EEEEEE 1px solid;
		float: left;
	}

	.card:last-of-type {
		float: right;
	}

	.goods {
		width: 704rpx;
		height: 586rpx;
		border-bottom: 1px solid #e5e5e5;
		margin: auto;
		margin-bottom: 50rpx;
	}

	.goodsimg {
		width: 704rpx;
		height: 352rpx;
	}

	.goodsname {
		// padding-left: 13rpx;
		margin-top: 20rpx;
	}

	.jindubox {
		width: 100%;
		height: 30rpx;
		line-height: 30rpx;
	}

	.jindu {
		width: 583rpx;
	}

	.status {
		color: #676767;
		font-size: 26rpx;
	}

	.bottombox {
		margin-top: 30rpx;
		height: 100rpx;
	}

	.miao {
		color: #DF2911;
		font-size: 26rpx;
	}

	.miaop {
		font-size: 36rpx;
		color: #DF2911;
	}

	.notice {
		color: #7B7B7B;
		font-size: 20rpx;
		margin-top: 15rpx;
	}

	.btns {
		width: 128rpx;
		height: 40rpx;
		background: #fd5052;
		border-radius: 20rpx;
		text-align: center;
		line-height: 40rpx;
		color: white;
		font-size: 24rpx;
		margin-top: 60rpx;
	}

	.nums {
		color: #DF2911;
		font-size: 24rpx;
		margin-top: 10rpx;
	}

	.jjkq {
		margin-top: 40rpx;
	}

	.jjkqbtn {
		margin-top: 50rpx;
	}
</style>
