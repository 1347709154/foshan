<template>
	<view class="content">
		<view class="top">
			<!-- 搜索 -->
			<view class="search">
				<u-search placeholder="请输入志愿者关键字" shape="square"></u-search>
			</view>
			<!-- 导航 -->
			<view class="nav">
				<view class="nav-ul" @tap="change(0)" :class="[btnnum=='0'?'active':'']">招募信息</view>
				<view class="nav-ul" @tap="change(1)" :class="[btnnum=='1'?'active':'']">活动信息</view>
				<view class="nav-ul" @tap="change(2)" :class="[btnnum=='2'?'active':'']">志愿者风采</view>
			</view>
		</view>
		<view class="body">
			<view v-if="btnnum==0">
				<view>佛顶山学雷锋志愿者服务队 </view>
				<view>【招募对象】</view>
				<view>1、热爱旅游，文化等人士优先。 　2、身心健康，宽厚随和，有较强的责任心和团队意识，有较好的语言表达能力及沟通能力，普通话标准。 　3、年龄18岁以上。 　4、能按照规定时间来园服务。 　5、遵守佛顶山旅游管理处的各项规章制度。 　【招募类别】 　1、景区导览志愿者 　在景区为游客提供免费讲解，义务指路、活动信息咨询、文化活动宣传等服务，并协助工作人员维持秩序，完善游客的游园体验，实时为游客提供便利。 　2、展厅讲解志愿者 　在展厅为游客解读展览，传播历史文化知识，增进游客参观体验，维护展厅秩序，实时疏散游客。 　【联系我们】 　志愿者招募咨询电话 　关于景区导览志愿者招募咨询请致电xxxxxx，联系人XX 　咨询时间：9：00-11:00 13:00-16:00（周一至周五）</view>
			</view>
			<view v-if="btnnum==1">
				<view>为营造文明旅游的氛围，五一假期期间，县文化旅游体育局组织文明旅游志愿服务队来到明堂山、天峡等景区开展文明旅游劝导活动。 在景区内，为提升广大游客的文明旅游意识，志愿者们帮助维持入园秩序，帮助游客开通健康码，有序入园，提醒游客戴好口罩，保持适当距离，宣传文明出游注意事项，引导游客文明旅游，展现了文明旅游志愿者的风采。</view>
			</view>
			<view v-if="btnnum==2">
				<view class="body-list" v-for="(item,index) in lsit" @tap="details">
					<view class="body-list-img">
						<image class="user_img" :src="item.img" mode="aspectFit"></image>
					</view>
					<view class="user_message">
						<view class="" style="font-size: 32rpx;font-weight: bold;">{{item.user_name}}</view>
						<view class="user_message-ul">服务地区：{{item.address}}</view>
						<view class="user_message-ul">服务领域：{{item.field}}</view>
						<view class="user_message-ul">身份属性：{{item.uid}}</view>
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
				btnnum:0,
				lsit:[
					{
						img:"../../static/user/user_img.png",
						user_name:"王甜",
						address:"景区",
						field:"帮困，文明指导，语言服务",
						uid:"青年"
					},{
						img:"../../static/user/user_img.png",
						user_name:"王甜",
						address:"景区",
						field:"帮困，文明指导，语言服务",
						uid:"青年"
					},{
						img:"../../static/user/user_img.png",
						user_name:"王甜",
						address:"景区",
						field:"帮困，文明指导，语言服务",
						uid:"青年"
					}
				]
			}
		},
		onLoad() {

		},
		methods: {
			// 顶部导航切换
			change(e) {
				this.btnnum = e
			},
			//跳转志愿者详情
			details:function(e){
				uni.navigateTo({
					url:"/pages/volunteer/details"
				})
			}
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	.top{
		display: flex;
		flex-direction: column;
		width: 100%;
		align-items: center;
		justify-content: center;
		position: fixed;
		top: 44px;
		left: 0;
		z-index: 99999;
		background: #ffffff;
	}
	/* 搜索 */
	.search{
		width: 96%;
		height: 80rpx;
		box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
		display: flex;
		justify-content: center;
		align-items: center;
	}
	/*  导航*/
	.nav{
		width: 96%;
		height: 100rpx;
		line-height: 100rpx;
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
		border-bottom: 1rpx solid #EEEEEE;
	}
	.nav-ul{
		float: left;
		width: 33.3%;
		height: 100rpx;
		text-align: center;
		display: inline-block;
		color: #676767;
		line-height: 100rpx;
	}
	.active{
		display: inline-block;
		height: 96rpx;
		line-height: 98rpx;
		color: #FE0000;
	}
	/* 正文 */
	.body{
		width: 96%;
		margin-top: 180rpx;
		padding: 20rpx;
	}
	.body>view>view{
		margin-top: 20rpx;
	}
	.body-list{
		display: flex;
		flex-direction: row;
		border-bottom: 1rpx solid #ddd;
		padding: 20rpx;
	}
	.user_img{
		width: 120rpx;
		height: 150rpx;
	}
	.user_message{
		display: flex;
		flex-direction: column;
		
	}
	.user_message>view{
		margin-left: 20rpx;
		margin-top: 10rpx;
	}
	.user_message-ul{
		font-size: 26rpx;
		color: #858585;
	}
</style>
