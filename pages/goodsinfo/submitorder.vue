<template>
	<view class="content">
		<view class="topbox">
			<p id="title">{{title}}</p>
			<p id="key"><span v-for="item in key">{{item}}</span></p>
			<p id="date">选择日期</p>
			<view class="datelist">
				<!-- 写入自定义对象的属性判断是否为选中 -->
				<view :class="[item.isflag==true?'time':'time2']" v-for="(item,index) in datelist" @tap="change(index)">
					<p>{{item.date}}</p>
					<p>{{item.time}}</p>
					<view class="redbox">
						<image src="../../static/order/yes.png" mode="" class="yes"></image>
					</view>
				</view>
			</view>
			<view class="count">
				<view class="left text">
					选择数量
				</view>
				<view class="right countnum">
					<u-number-box v-model="value" @change="valChange"></u-number-box>
				</view>
			</view>
			<p id="copn">优惠</p>
			<view class="cponlist">
				<view class="left bg">
					券
				</view>
				<view class="left textleft">
					优惠券
				</view>
				<view class="right gouse">
					去使用
				</view>
			</view>
		</view>
		<view class="tourist">
			<p id="tourist">游客信息</p>
			<view class="touristbox">
				<view :class="[item.isflag==true?'listitem':'listitem2']" v-for="(item,index) in touristlist" @tap="change2(index),getinfo(index)">
					<p>{{item.name}}</p>
					<view class="redbox">
						<image src="../../static/order/yes.png" mode="" class="yes"></image>
					</view>
				</view>
				<view class="listitem3" @click="address()">
					<p>新增</p>
					<p>更换</p>
				</view>
			</view>
			<view class="bottombox" v-for="(it,ind) in touristlist " v-if="it.isflag==true">
				<view class="left headimg" >
					<p>游客</p>
					<!-- <image src="../../static/order/cha.png" mode="" id="headming"></image> -->
				</view>
				<view class="left touristinfo">
					<p class="infotext">{{it.name}}</p>
					<p class="infotext">{{it.phone}}</p>
					<p v-if="it.idnum==''" id="noidmun">缺少证件号，点击补齐</p>
					<p class="infotext" v-else>{{it.idnum}}</p>
				</view >
				<view class="right editbtn" @click="address(ind)">
					编辑
				</view>
			</view>
		</view>
		<view class="paybox">
			<view class="paylist">
				<view class="left">
					<view class="">
						<image src="../../static/order/wx.png" mode="" class=" payicon"></image>
					</view>
					<view class="">
						<image src="../../static/order/zfb.png" mode="" class=" payicon"></image>
					</view>
				</view>

				<view class="left paytext">
					<p class="text1">微信支付</p>
					<p class="text1">支付宝支付</p>
				</view>
				<view class="right radios">
					<u-radio-group  :wrap="true">
						<view class="radiobox">
							<u-radio shape="circle" @change="radioChange" :name="1" ></u-radio>
						</view>
						<view class="radiobox">
							<u-radio shape="circle" @change="radioChange" :name="2" ></u-radio>
						</view>
					</u-radio-group>
				</view>
			</view>

		</view>
		<view class="paybtns">
			<view class="left money">
				<p><span>总价¥</span><span>{{totalmoney}}</span></p>
			</view>
			<view class="right btns">
				<view class="btn-b left">
					
							分享
					
					<image src="../../static/food/share.png" mode=""class="right share"></image>
				
				</view>
				<view class="btn-r right" @tap="gettitkt">
					提交订单
				</view>
			</view>
		</view>
		<u-popup v-model="show" mode="bottom" class="pop" height="450rpx" :closeable="true">
			<view class="pop-tel">填写信息</view>
			<u-field v-model="name" label="姓名" placeholder="请填写姓名"></u-field>
			<u-field v-model="phone" label="电话" placeholder="电话" type="number"></u-field>
			<u-field v-model="idnum" label="身份证" placeholder="身份证" type="idcard"></u-field>
			<!-- <input :value="touristlist[index].name" placeholder="请输入姓名" class="popup-input" />
			<input :value="touristlist[index].phone" placeholder="请输入联系电话" type="number"  class="popup-input"/>
			<input :value="touristlist[index].idnum" placeholder="请输入身份证" type="idcard"  class="popup-input"/> -->
			<view class="popup-bt" @click="Submit">确定</view>
		</u-popup>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				index:0,
				show:false,
				name:'',
				phone:'',
				idnum:'',
				paytype:'',
				// 步进器
				value: 1,
				number:1,
				title: '景区门票+旅游巴士+观光车票',
				key: ["无需退票", "退款无忧"],
				datelist: [{
						date: "5-19",
						time: '今天',
						isflag: false
					},
					{
						date: "5-20",
						time: '明天',
						isflag: false
					},
					{
						date: "5-21",
						time: '后天',
						isflag: false
					},
				],
				touristlist: [{
						name: '张三',
						phone: 17337477765,
						idnum: '4236481236489216349812394',
						isflag: false
					},
					{
						name: '李四',
						phone: 13452322453,
						idnum: '',
						isflag: false
					}
				],
				touristinfo: {},
				totalmoney:300
			};
		},
		onLoad(options){
			this.give_type=options.give_type;
		},
		methods: {
			// 更改属性值
			change(i) {
				console.log(i)
				for (var j = 0; j < this.datelist.length; j++) {
					this.$set(this.datelist[j], 'isflag', false)
				}
				this.$set(this.datelist[i], 'isflag', true)
			},
			change2(i) {
				if(this.touristlist[i].isflag==true){
					this.$set(this.touristlist[i], 'isflag', false)
					let num = this.value;
					 num=num-1;
	
					this.value = num
				}else{
					this.$set(this.touristlist[i], 'isflag', true);
					let num = 0;
					for(var j=0;j<this.touristlist.length;j++){
						console.log(11111)
						if(this.touristlist[j].isflag==true){
						  num=num+1;
						}
					}
					this.value = num
					
				}
			},
			// 获取用户信息
			getinfo(i) {
				this.touristinfo = this.touristlist[i]
			},
			// 获取步进器的值
			valChange(e) {
				console.log('当前值为: ' + e.value)
			},
			// 选中某个单选框时，由radio时触发
			// 获取支付方式
			radioChange(e) {
				console.log(e);
				this.paytype=e
			},
			// 跳转出票
			gettitkt(){
				uni.navigateTo({
					url:"/pages/guide-pre/pre?type=scenic"
				})
			},
			//新增或更换游客
			address:function(index){
				this.show  = true;
				if(index){
					this.name = this.touristlist[index].name
					this.phone = this.touristlist[index].phone
					this.idnum = this.touristlist[index].idnum
					this.index = index;
				}else{
					this.name = ''
					this.phone = ''
					this.idnum = ''
				}
				
				
			},
			Submit:function(e){
				if(this.index){
					this.touristlist[this.index].name = this.name
					this.touristlist[this.index].phone = this.phone
					this.touristlist[this.index].idnum = this.idnum
					this.show = false;
				}else{
					console.log(111111)
					let touristlist = this.touristlist
					let list = {}
						list.name = this.name
						list.phone = this.phone
						list.idnum=this.idnum
					touristlist.splice(0,0,list);
					this.touristlist = touristlist
					console.log(touristlist);
					this.show = false;
				}
				
			}
		}
	}
</script>

<style lang="scss">
	page {
		background: #f1f1f1;
	}
	.content{
		// position: relative;
	}
	.topbox {
		width: 717rpx;
		height: 487rpx;
		background: #FFFFFF;
		margin: auto;
		margin-top: 17rpx;
		border-radius: 8rpx;
	}

	#title {
		font-size: 30rpx;
		color: #000000;
		margin-top: 20rpx;
		margin-left: 20rpx;
	}

	#key {
		margin-top: 30rpx;
		margin-left: 20rpx;
		font-size: 24rpx;
		color: #000000;

		span {
			color: #000000;
			font-size: 18rpx;
			display: inline-block;
			width: 60px;
			border-right: 1px solid #000000;
			margin-right: 20rpx;
		}

		span:last-of-type {
			border-right: none;
			margin-right: 0;
		}
	}

	#copn {
		font-size: 30rpx;
		color: #000000;
		margin-top: 10rpx;
		margin-left: 20rpx;
	}

	#date {
		font-size: 30rpx;
		color: #000000;
		margin-top: 20rpx;
		margin-left: 20rpx;
	}

	.datelist {
		height: 67rpx;
		width: 100%;
		padding: 0 20rpx;
		display: flex;
		margin-top: 16rpx;
	}

	.time {
		width: 146rpx;
		position: relative;
		height: 67rpx;
		background: #FDE4E4;
		border: 1px solid #EF1E22;
		border-radius: 8rpx;
		margin-right: 20rpx;
		text-align: center;
		font-size: 24rpx;

		.redbox {
			width: 38rpx;
			height: 24rpx;
			background: #EF1E22;
			border-radius: 8rpx;
			position: absolute;
			right: 0;
			line-height: 24rpx;
			bottom: 0;

			.yes {
				width: 22rpx;
				height: 15rpx;
				margin-top: -20rpx;
			}
		}

		p {
			height: 16px;
		}
	}

	.time2 {
		width: 146rpx;
		height: 67rpx;
		background: none;
		border: 1px solid #F1F1F1;
		color: #F1F1F1;
		border-radius: 8rpx;
		margin-right: 20rpx;
		text-align: center;
		font-size: 24rpx;

		.redbox {
			display: none;
		}

		p {
			height: 16px;
		}
	}

	.count {
		height: 52rpx;
		margin-top: 30rpx;
		padding-left: 20rpx;
		padding-right: 43rpx;
		line-height: 52rpx;
	}

	.text {
		font-size: 30rpx;
		color: #000000;

		// padding-left: 20rpx;
	}

	.cponlist {
		width: 694rpx;
		height: 70rpx;
		background: #F6F3F3;
		border-radius: 6rpx;
		margin: auto;
		// margin-top: 10rpx;
	}

	.bg {
		width: 20rpx;
		height: 20rpx;
		font-size: 18rpx;
		font-weight: bold;
		line-height: 20rpx;
		color: #FF0101;
		background: #FDCECE;
		margin-top: 18rpx;
		margin-left: 12rpx;
	}

	.textleft {
		margin-left: 9rpx;
		line-height: 70rpx;
		font-weight: 500;
	}

	.gouse {
		margin-right: 43rpx;
		line-height: 70rpx;
		font-weight: 500;
		color: #4A4A4A;
		font-size: 26rpx;
	}

	.tourist {
		width: 717rpx;
		margin: auto;
		margin-top: 9rpx;
		padding-bottom: 30rpx;
		background: #FFFFFF;
		border-radius: 8rpx;
	}

	#tourist {
		font-size: 30rpx;
		color: #000000;
		margin-top: 20rpx;
		margin-left: 20rpx;
	}

	.touristbox {
		font-size: 24rpx;
		height: 67rpx;
		width: 100%;
		padding: 0 20rpx;
		display: flex;
		margin-top: 14rpx;
	}

	.listitem {
		width: 146rpx;
		height: 67rpx;
		background: #FDE4E4;
		border: 1px solid #EF1E22;
		border-radius: 8rpx;
		text-align: center;
		line-height: 67rpx;
		margin-right: 20rpx;
		position: relative;

		.redbox {
			width: 38rpx;
			height: 24rpx;
			background: #EF1E22;
			border-radius: 8rpx;
			position: absolute;
			right: 0;
			line-height: 24rpx;
			bottom: 0;

			.yes {
				width: 22rpx;
				height: 15rpx;
				margin-top: -20rpx;
			}
		}
	}

	.listitem2 {
		width: 146rpx;
		height: 67rpx;
		background: #FFFFFF;
		border: 1px solid #E5E5E5;
		border-radius: 8rpx;
		font-size: 24rpx;
		margin-right: 20rpx;
		text-align: center;
		line-height: 67rpx;

		.redbox {
			display: none;
		}
	}

	.listitem3 {
		width: 146rpx;
		height: 67rpx;
		background: #FFFFFF;
		border: 1px solid #E5E5E5;
		border-radius: 8rpx;
		font-size: 22rpx;
		margin-right: 20rpx;
		text-align: center;
		// line-height: 67rpx;
	}

	.bottombox {
		height: 180rpx;
		width: 681rpx;
		margin: auto;
		border-top: 1px solid #e5e5e5;
		margin-top: 30rpx;
	}

	.headimg {
		width: 60rpx;
		height: 180rpx;
		// line-height: 180rpx;
		text-align: center;
		margin-left: 28rpx;
		padding-top: 60rpx;
		font-size: 24rpx;

	}

	#headming {
		width: 24rpx;
		height: 23rpx;
	}

	.editbtn {
		line-height: 180rpx;
		font-size: 24rpx;
		color: #379BF8;
		margin-right: 20rpx;
	}

	.touristinfo {
		margin-left: 40rpx;
		margin-top: 20rpx;
	}

	.infotext {
		font-size: 28rpx;
		line-height: 50rpx;
	}

	#noidmun {
		color: #F60D0D;
		font-size: 28rpx;
	}

	.paylist {
		padding-left: 40rpx;
	}

	.paybox {
		width: 715rpx;
		height: 210rpx;
		background: #FFFFFF;
		border-radius: 30rpx;
		margin-top: 15rpx;
	}

	.payicon {
		width: 49rpx;
		margin-top: 30rpx;
		height: 49rpx;
	}

	.text1 {
		height: 49rpx;
		margin-top: 35rpx;
	}

	.paytext {
		margin-left: 17rpx;
		// margin-top: 30rpx;
		// line-height: 75rpx;
	}

	.radios {
		width: 40rpx;
		height: 210rpx;
		margin-top: 20rpx;
		margin-right: 60rpx;
	}

	.radiobox {
		height: 90rpx;
	}
	.paybtns{
		width: 100%;
		height: 105rpx;
		line-height: 105rpx;
		background: #FFFFFF;
		position: fixed;
		padding: 0 20rpx;
		bottom: 0;
		left: 0;
		p span:first-of-type{
			font-size: 24rpx;
			color: #f60000;
		}
		p span:last-of-type{
			font-size: 42rpx;
			color: #f60000;
		}
	}
	.btns{
		width: 509rpx;
		height: 78rpx;
		line-height: 78rpx;
		font-size: 24rpx;
		margin-top: 17rpx;
	}
	.btn-b{
		height: 100%;
		width: 230rpx;
		background: #0A0000;
		color: white;
		border-radius: 39rpx 0px  0px 39rpx;
		text-align: center;
		position: relative;
	}
	.btn-r{
		height: 100%;
		width: 279rpx;
		text-align: center;
		background: #EF1E22;
		color: white;
		border-radius: 0px 39rpx 39rpx 0px;
	}
	.share{
		width: 32rpx;
		height: 32rpx;
		// margin-right:60rpx;
		margin-top: 23rpx;
		right: 50rpx;
		position: absolute;
	}
	.pop{
		padding-top: 50rpx;
	}
	.pop-tel{
		height: 100rpx;
		text-align: center;
		line-height: 100rpx;
		width: 100%;
		border-bottom: 1rpx solid #ddd;
	}
	.popup-bt{
		height: 80rpx;
		line-height: 80rpx;
		width: 100%;
		background:#FF9726 ;
		margin-top: 20rpx;
		// opacity: 0.5;
		text-align: center;
		color: #FFFFFF;
	}
</style>
