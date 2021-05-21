<template>
	<view class="content">
		<view class="houseinfo">
			<view class="timebox">
				<view class="left stime">
					{{time.stime}}
				</view>
				<view class="left greytext">
					今天
				</view>
				<view class="left totaltime">
					一晚
				</view>
				<view class="left etime">
					{{time.etime}}
				</view>
				<view class=" left greytext">
					明天
				</view>
			</view>
			<p>{{houseinfo.name}}</p>
			<p id="tags">
				<span>{{houseinfo.size}}㎡</span>
				<span v-for="(item,index) in houseinfo.tag">
					<span v-if="index==item.length">
						{{item}}
					</span>
					<span v-else>
						{{item}}·
					</span>
				</span>
			</p>
			<view class="notice">
				<image src="../../static/scenic/zhengque.png" mode="" class="left"></image>
				<span>入住当天18:00前可免费取消</span>
			</view>
		</view>
		<view class="orderinfo">
			<!-- <u-cell-group>
					<u-cell-item title="房间数量" :center="true" >{{houseinfo.roomnum}}间</u-cell-item>
					<u-cell-item title="住客姓名" :center="true" :arrow="false">{{houseinfo.roomown}}</u-cell-item>
					<u-cell-item title="联系电话" :center="true" >{{houseinfo.phone}}</u-cell-item>
					<u-cell-item title="预计到店" :center="true" >{{houseinfo.time}}</u-cell-item>
				</u-cell-group> -->
			<u-field label="房间数量" right-icon="arrow-right" :disabled="true" v-model="houseinfo.roomnum"></u-field>
			<u-field label="住客姓名" :disabled="true" v-model="houseinfo.roomown"></u-field>
			<u-field label="联系电话" right-icon="arrow-right" :disabled="true" v-model="houseinfo.phone"></u-field>
			<u-field label="预计到店" right-icon="arrow-right" :disabled="true" v-model="houseinfo.time"></u-field>
		</view>
		<view class="priceinfo">
			<u-field label="费用明细" :disabled="true"></u-field>
			<view class="orderinfo2">
				<view class="left title">
					在线支付
				</view>
				<view class="right time">
					<p><span class="type">{{houseinfo.totaltime}}</span><span class="redtext">¥{{houseinfo.totalprice}}</span></p>
				</view>
			</view>
			<view class="oederinfo">
				<view class="li toptitle">
					<view class="left">
						房费
					</view>
					<view class="right">
						¥{{houseinfo.totalprice}}
					</view>
				</view>
				<view class="li infotext">
					<view class="left">
						<p><span class="left">{{time.year}}-{{time.month}}-{{time.day}}</span> <span class="keywods right">{{houseinfo.keys}}</span></p>
						<p><span class="left">{{time.year}}-{{time.month}}-{{time.day+1}} </span><span class="keywods right">{{houseinfo.keys}}</span></p>
					</view>
					<view class="right">
						<span id="num">{{houseinfo.housetotal}}x</span>
						<span>¥{{houseinfo.unit}}</span>
					</view>
				</view>
			</view>
		</view>
		<view class="noticelist">
			<view class="bigtitle">
				重要提示
			</view>
			<view class="rule">
				<p class="stitle">退款规则</p>
				<p class="info">根据民宿政策，<span>{{time.stime}}</span>18点前可免费取消，逾期不可取消/变更，如未 入住，民宿将扣除全部房费</p>
			</view>
			<view class="rule2">
				<p class="stitle">预定说明</p>
				<p class="info">订单需等民宿确认后才生效，订单确认结果以短信通知为准；请在订单 生效后再至民宿前台办理入住。</p>
			</view>
		</view>
		<view  :class="[show==true?'submitorder1':'submitorder']">
			<view class="box-info" v-if="show==true">
				<view class="orderinfo2">
					<view class="left title">
						在线支付
					</view>
					<view class="right time">
						<p><span class="type">{{houseinfo.totaltime}}</span><span class="redtext">¥{{houseinfo.totalprice}}</span></p>
					</view>
				</view>
				<view class="oederinfo">
					<view class="li toptitle">
						<view class="left">
							房费
						</view>
						<view class="right">
							¥{{houseinfo.totalprice}}
						</view>
					</view>
					<view class="li infotext">
						<view class="left">
							<p><span class="left">{{time.year}}-{{time.month}}-{{time.day}}</span> <span class="keywods right">{{houseinfo.keys}}</span></p>
							<p><span class="left">{{time.year}}-{{time.month}}-{{time.day+1}} </span><span class="keywods right">{{houseinfo.keys}}</span></p>
						</view>
						<view class="right">
							<span id="num">{{houseinfo.housetotal}}x</span>
							<span>¥{{houseinfo.unit}}</span>
						</view>
					</view>
				</view>
			</view>
			<view class="left pricebox">
				<view class="left redprice">
					<span>¥</span><span id="bigtext">{{houseinfo.totalprice}}</span>
				</view>
				<view class="right priceinfobtn" @tap="change">
					<span class="left">明细</span>
					<image src="../../static/scenic/zhankai.png" mode="" class="left zhan" v-if="show==false"></image>
					<image src="../../static/scenic/shouqi.png" mode="" class="left zhan" v-else></image>
				</view>
			</view>
			<view class="right submit" @tap="getqrcode">
				提交订单
			</view>
		</view>
		<u-mask :show="show" @click="show = false" z-index="4" duration="100"></u-mask>
	</view>
	
</template>

<script>
	export default {
		data() {
			return {
				houseinfo: {
					name: '灵动大床房',
					tag: ['无早餐', '大床有窗', '2人住', '可吸烟'],
					size: 12,
					roomnum: 1,
					roomown: '张三',
					phone: 15255667788,
					time: '14:00',
					totaltime: '一间一晚',
					totalprice: 228,
					unit: 228,
					housetotal: 1,
					keys: '无早餐'

				},
				time: {
					stime: '',
					etime: '',
					month: '',
					year: '',
					day: ''
				},
				show:false
			};
		},
		onLoad(option) {
			uni.setNavigationBarTitle({
				title: option.name
			})
		},
		methods: {
			getdate() {
				var datetime = new Date();
				var year = datetime.getFullYear();
				var month = datetime.getMonth() + 1 < 10 ? "0" + (datetime.getMonth() + 1) : datetime.getMonth() + 1;
				var date = datetime.getDate() < 10 ? "0" + datetime.getDate() : datetime.getDate();
				console.log(month, date)
				this.time.stime = month + '月' + date + '日'
				this.time.etime = month + '月' + (date + 1) + '日'
				this.time.year = year,
					this.time.month = month,
					this.time.day = date
			},
			change(){
				this.show=!this.show
			},
			getqrcode(){
				uni.navigateTo({
					url:"/pages/guide-pre/pre?type=hotel"
				})
			}
		},
		mounted() {
			this.getdate()
		}
	}
</script>

<style lang="scss">
	page {
		background: #F1F1F1;
	}

	.content {
		position: relative;
	}

	.houseinfo {
		width: 675rpx;
		height: 195rpx;
		background: rgba(255, 255, 255, 0.45);
		border-radius: 7rpx;
		padding-left: 17rpx;
	}

	.timebox {
		height: 40rpx;
		font-size: 24rpx;
		color: #010101;
		margin-top: 19rpx;
	}

	.greytext {
		margin-left: 10rpx;
	}

	.totaltime {
		width: 60rpx;
		height: auto;
		color: #010101;
		border: 1px solid #000000;
		border-radius: 10px;
		text-align: center;
		font-size: 18rpx;
		margin: 0 20rpx;
	}

	#tags {
		font-size: 20rpx;
		color: #6D6B6B;
	}

	.notice {
		width: 636rpx;
		height: 65rpx;
		border-top: 1px solid #e5e5e5;
		margin-top: 5rpx;
		line-height: 65rpx;

		image {
			width: 23rpx;
			height: 24rpx;
			margin-top: 20rpx;
		}

		font-size: 20rpx;
		color: #000000;

		span {
			margin-left: 5rpx;
		}
	}

	.orderinfo {
		width: 675rpx;
		height: 359rpx;
		background: rgba(255, 255, 255, 0.45);
		border-radius: 7rpx;
		margin-top: 13rpx;
		padding: 0 20rpx;
	}

	.priceinfo {
		padding: 0 20rpx;
		width: 675rpx;
		height: 345rpx;
		background: rgba(255, 255, 255, 0.45);
		border-radius: 7rpx;
		margin-top: 13rpx;
	}

	.orderinfo2 {
		height: 76rpx;
		border-bottom: 1px solid #e5e5e5;
		line-height: 76rpx;
	}

	.title {
		margin-left: 30rpx;
	}

	.time {
		color: #000000;
		font-size: 30rpx;

		.redtext {
			color: #FF0000;
		}
	}

	.type {
		margin-right: 20rpx;
	}

	.oederinfo {
		height: 187rpx;
	}

	.li {
		height: 60rpx;
		padding-left: 30rpx;
	}

	.toptitle {
		margin-top: 30rpx;
	}

	.infotext {
		font-size: 20rpx;
		color: #2c2c2c;
	}

	#num {
		margin-right: 10rpx;
	}

	.keywods {
		margin-left: 20rpx;
	}

	.noticelist {
		width: 675rpx;
		height: 378rpx;
		background: rgba(255, 255, 255, 0.45);
		border-radius: 7rpx;
		margin-top: 13rpx;
		margin-bottom: 118rpx;
		padding: 0 20rpx;
	}

	.bigtitle {
		height: 80rpx;
		border-bottom: 1px solid #e5e5e5;
		line-height: 80rpx;
		padding-left: 20rpx;
	}

	.rule {
		height: 148rpx;
		border-bottom: 1px solid #e5e5e5;
		padding-left: 20rpx;
	}

	.rule2 {
		height: 148rpx;
		// border-bottom: 1px solid #e5e5e5;
		padding-left: 20rpx;
	}

	.stitle {
		font-size: 24rpx;
		color: #000000;
		padding-top: 15rpx;
	}

	.info {
		font-size: 20rpx;
		color: #2f2f2f;
		margin-top: 15rpx;
	}

	.submitorder {
		width: 100%;
		height: 98rpx;
		background: #FFFFFF;
		position: fixed;
		left: 0;
		bottom: 0;
	}
	.submitorder1 {
		width: 100%;
		z-index: 5;
		height: 390rpx;
		background: #FFFFFF;
		position: fixed;
		left: 0;
		bottom: 0;
		.box-info{
			padding: 0 50rpx;
			height: 292rpx;
			border-radius: 28rpx 28rpx 0px 0px;
			.redtext{
				color: #000000;
			}
		}
	}
	.submit {
		line-height: 98rpx;
		background: #E50505;
		color: #FFFFFF;
		text-align: center;
		width: 340rpx;
		font-size: 36rpx;

	}

	.pricebox {
		line-height: 98rpx;
		width: 410rpx;
	}

	.redprice {
		margin-left: 75rpx;
		color: #FF0B0B;
	}

	#bigtext {
		font-size: 53rpx;
	}

	.priceinfobtn {
		margin-right: 30rpx;
		line-height: 98rpx;
	}

	.zhan {
		width: 20rpx;
		height: 11rpx;
		margin-top: 48rpx;
		margin-left: 10rpx;
	}
</style>
