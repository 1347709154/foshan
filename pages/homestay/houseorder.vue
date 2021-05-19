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
				<span v-for="(item,index) in houseinfo.tag" >
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
				<u-field label="房间数量" right-icon	="arrow-right" :disabled="true" v-model="houseinfo.roomnum"></u-field>
				<u-field label="住客姓名" :disabled="true" v-model="houseinfo.roomown"></u-field>
				<u-field label="联系电话" right-icon	="arrow-right" :disabled="true" v-model="houseinfo.phone"></u-field>
				<u-field label="预计到店" right-icon	="arrow-right" :disabled="true" v-model="houseinfo.time"></u-field>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				houseinfo:{
					name:'灵动大床房',
					tag:['无早餐','大床有窗','2人住','可吸烟'],
					size:12,
					roomnum:1,
					roomown:'张三',
					phone:15255667788,
					time:'14:00'
				},
				time: {
					stime: '',
					etime: '',
				}
			};
		},
		onLoad(option) {
			uni.setNavigationBarTitle({
				title:option.name
			})
		},
		methods:{
			getdate() {
				var datetime = new Date();
				var year = datetime.getFullYear();
				var month = datetime.getMonth() + 1 < 10 ? "0" + (datetime.getMonth() + 1) : datetime.getMonth() + 1;
				var date = datetime.getDate() < 10 ? "0" + datetime.getDate() : datetime.getDate();
				console.log(month, date)
				this.time.stime = month + '月' + date + '日'
				this.time.etime = month + '月' + (date + 1) + '日'
			},
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
	.houseinfo{
		width: 675rpx;
		height: 195rpx;
		background: rgba(255, 255, 255, 0.45);
		border-radius: 7rpx;
		padding-left: 17rpx;
	}
	.timebox{
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
	#tags{
		font-size: 20rpx;
		color: #6D6B6B;
	}
	.notice{
		width: 636rpx;
		height: 65rpx;
		border-top: 1px solid #e5e5e5;
		margin-top: 5rpx;
		line-height: 65rpx;
		image{
			width: 23rpx;
			height: 24rpx;
			margin-top: 20rpx;
		}
		font-size: 20rpx;
		color: #000000;
		span{
			margin-left: 5rpx;
		}
	}
	.orderinfo{
		width: 675rpx;
		height: 359rpx;
		background: rgba(255, 255, 255, 0.45);
		border-radius: 7rpx;
		margin-top: 13rpx;
	}
	.u-cell__value{
		text-align: left;
		padding-left: 80rpx;
	}
</style>
