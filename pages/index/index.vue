<template>
	<view class="home">
		<view class="header">
			<view class="header_block">
				<image  src="../../static/banner.png" mode="scaleToFill"></image>
				<view class="con">
					<view>16 - 27℃</view>
					<view>佛顶山生态旅游区</view>
					<view class="bigtitle">旅居天堂，康养圣地</view>
				</view>
			</view>
			
		</view>
		<view class="home_center">
			<view class="centerlist">
				<view class="center_item" v-for="(item,index) in list">
					<view class="item_list">
						<image class="itemicon"  
						:src="item.img"
						 mode="widthFix"></image>
						 <view>{{item.title}}</view>
					</view>
				</view>
				
			</view>
			<!-- 购票 导游预约 -->
			<view class="pay_piao">
				<view class="yuyue">
					<view class="goupiao_con">
						<view class="title">购票</view>
						<view class="miaosu">购票轻松游</view>	
					</view>
					<image class="icon" src="../../static/home/goupiao.png" mode="widthFix"></image>
				</view>
				<view class="yuyue">
					<view class="goupiao_con">
						<view class="title">导游预约</view>
						<view class="miaosu">轻松了解民俗文化</view>
					</view>
					<image class="icon" src="../../static/home/daoyou.png" mode="widthFix"></image>
				</view>
			</view>
			<!-- 景区介绍 -->
			<view class="qujs">
				<view class="qujs_item"><text>景区介绍</text></view>
				<view class="qujs_item"><text>开放时间：</text>周一~周日08:00~18:00</view>
				<view class="qujs_item gengduo_more" >
					<view>
						<text>地址：</text> 贵州省铜仁市石阡县
					</view>
					<image class="gengduo" src="../../static/home/gengduo.png" mode="widthFix"></image>
				</view>
				<view class="jqxq">
					<text>景区详情</text>
					<view class="jqxq_border"></view>
				</view>
			</view>
		</view>
		<!-- 精彩视频 -->
		<view class="jingcai_video">
			<view class="block">
				<view class="title">
					<view class="title_icon"></view>
					<text>精彩视频</text>
				</view>
				<view class="more">
					<text>更多</text>
					<image class="moreicon gengduo" src="../../static/home/gengduo_.png" mode="widthFix"></image>
				</view>
			</view>
			<view class="video">
				<scroll-view scroll-x="true">
					<view class="item_video">
						<image class="image" src="../../static/home/bg1.png" mode="scaleToFill"></image>
						<view class="item_video_block">
							<image class="baofang" src="../../static/home/baofang.png" mode=""></image>
						</view>
					</view>
					<view class="item_video">
							<image class="image"  src="../../static/home/bg2.png" mode="widthFix"></image>
							<view class="item_video_block">
								<image class="baofang" src="../../static/home/baofang.png" mode=""></image>
							</view>
					</view>
					<view class="item_video">
						<image class="image" src="../../static/home/bg3.png" mode="widthFix"></image>
						<view class="item_video_block">
							<image class="baofang" src="../../static/home/baofang.png" mode=""></image>
						</view>
					</view>
				</scroll-view>
			</view>
			
		</view>
		
		<!-- 必玩景区 -->
		<view class="biwan jingcai_video">
			<view class="block">
				<view class="title">
					<view class="title_icon"></view>
					<text>必玩景区</text>
				</view>
				<view class="more">
					<text>更多</text>
					<image class="moreicon gengduo" src="../../static/home/gengduo_.png" mode="widthFix"></image>
				</view>
			</view>
			<view class="biwan_img video">
				<scroll-view scroll-x="true">
					<view class="item_video">
						<image class="image" src="../../static/home/bg1.png" mode="scaleToFill"></image>
						 <view class="title">金顶云海</view>
					</view>
					<view class="item_video">
						<image class="image"  src="../../static/home/bg2.png" mode="scaleToFill"></image>
						 <view class="title">金顶云海</view>
					</view>
					<view class="item_video">
						<image class="image" src="../../static/home/bg3.png" mode="scaleToFill"></image>
						 <view class="title">金顶云海</view>
					</view>
				</scroll-view>
			</view>
			
		</view>
		<!-- 民俗风情 -->
		<view class="biwan jingcai_video">
			<view class="block">
				<view class="title">
					<view class="title_icon"></view>
					<text>民俗风情</text>
				</view>
				<view class="more">
					<text>更多</text>
					<image class="moreicon gengduo" src="../../static/home/gengduo_.png" mode="widthFix"></image>
				</view>
			</view>
			<view class="biwan_img video">
				<scroll-view scroll-x="true">
					<view class="item_video">
						<image class="image" src="../../static/home/bg1.png" mode="scaleToFill"></image>
						 <view class="title">金顶云海</view>
					</view>
					<view class="item_video">
						<image class="image"  src="../../static/home/bg2.png" mode="scaleToFill"></image>
						 <view class="title">金顶云海</view>
					</view>
					<view class="item_video">
						<image class="image" src="../../static/home/bg3.png" mode="scaleToFill"></image>
						 <view class="title">金顶云海</view>
					</view>
				</scroll-view>
			</view>
			
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list:[
					{
						img:'../../static/home/lvyougonglv.png',
						title:'路由攻略'
					},{
						img:'../../static/home/techan.png',
						title:'当地特产'
					},{
						img:'../../static/home/dingzhiyou.png',
						title:'定制游'
					},{
						img:'../../static/home/minsu.png',
						title:'民宿客栈'
					},{
						img:'../../static/home/meishi.png',
						title:'美食必享'
					},{
						img:'../../static/home/xianshihuodong.png',
						title:'限时活动'
					},{
						img:'../../static/home/gongg.png',
						title:'公告'
					},
				]
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style>
	
	.home {
		background-color: #F2F2F2;
		display: flex;
		flex-direction: column;
	}
	.header{
		 position: relative;
		 display: flex;
		 flex-direction: column;
		 width: 100%;
		 width: 100%;
		 height: 400rpx;
	
	}
	.header_block image{
		position: absolute;
		left: 0;
		top: 0;
		width: 100%;
		height: 400rpx;
		z-index: 1;
	}
	
	.header_block .con{
		position: absolute;
		z-index: 1;
		color: #FFFFFF;
		bottom: 80rpx;
		margin-left: 30rpx;
	}
	.bigtitle{
		font-size: 50rpx;
		font-family:'SimHei';
		letter-spacing: 5rpx;
		margin: 30rpx 0;
	}
	.home_center{
		padding: 20rpx;
		z-index: 11;
		border-radius: 10rpx;
		background-color: #FFFFFF;
		margin: 0 30rpx;
		margin-top: -70rpx;
		display: flex;
		flex-direction: column;
	}
	.home_center .centerlist{
		
		flex: 1;
		display: flex;
		flex-wrap: wrap;
	}
	.center_item{
		width: 25%;
		margin: 10rpx 0;
	}
	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.itemicon{
		width: 60rpx;
		height: 60rpx;
		margin: 10rpx 0;
	}
	.item_list{
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		color: #3F3636;
		margin: 10rpx 0;
		font-size: 26rpx;
		
	}
	.pay_piao{
		display: flex;
		margin: 20rpx 0;
	}
	.yuyue
	{
		color: #FFFFFF;
		flex: 1;
		font-size: 30rpx;
		display: flex;
		padding: 20rpx;
		align-items: center;
		border-radius: 10rpx;
		background: linear-gradient(left,#5CC25F,#A8D16F);
	}
	.yuyue:first-child{
		margin-right: 20rpx;
	}
	.icon{
		width: 65rpx;
	}
	.goupiao_con{
		flex: 1;
		display: flex;
		flex-direction: column;
		
		
	}
	.goupiao_con .title{
		
		font-weight: bold;
		margin: 5rpx 0;
	}
	.miaosu{
		
		margin-right: 10rpx;
		font-size: 20rpx;
		letter-spacing: 2rpx;
	}
	.qujs{
		font-size: 26rpx;
	}
	.qujs text{
		font-weight: bold;
	}
	.qujs_item{
		line-height: 60rpx ;
		display: flex;
		align-items: center;
		
	}
	.gengduo_more{
		display: flex;
		justify-content: space-between;
		border-bottom: 1rpx solid #F7F7F7;
		padding-bottom: 10rpx;
	}
	.gengduo{
		width: 10rpx;
		float: right;
		margin: 0 50rpx;
	}
	.jqxq{
		text-align: center;
		font-weight: bold;
		line-height:40rpx;
		margin: 10rpx 0;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	.jqxq_border{
		background:#D4D4D4;
		width: 50rpx;
		height: 4rpx;
	}
	.jingcai_video{
		display: block;
		padding: 20rpx 30rpx;
		background-color: #FFFFFF;
		margin-top: 30rpx;
		
	}
	.block{
		display: flex;
		justify-content: space-between;
	}
	.jingcai_video .title{
		font-size: 35rpx;
		font-weight: bold;
		display: flex;
	}
	.title_icon{
		width: 6rpx;
		height: 100%;
		background: #009944;
		margin-right: 20rpx;
	}
	.more{
		display: flex;
		align-items: center;
		color: #009944;
		font-size: 28rpx;
	}
	.moreicon{
		margin: 0 10rpx;
	}
	.video{
		width: 100%;
		display: flex;
		white-space: nowrap;
		height: 300rpx;
		margin: 30rpx 0;
	}
	.biwan{
		
	}
	.image{
		margin: 10rpx 0;
		width:100%;
		border: none;
		height: 280rpx;
		position: absolute;
		
	}
	scroll-view{
		width: 100%;
		height: 300rpx;
		white-space: nowrap;
		
	}
	.baofang{
		
		width: 100rpx;
		height: 100rpx;
		border-radius: 100%;
		z-index: 15;
	}
	.item_video{
		
		position: relative;
		display: inline-block;
		width: 80%;
		height: 100%;
		margin: 0 20rpx;
		background-color: #000000;
		border-radius: 15rpx;
		overflow: hidden;
		
	}
	.item_video_block{
		display: flex;
		border: 1rpx solid red;
		justify-content: center;
		align-items: center;
		height: 100%;
	}
	.item_video:first-child{
		margin-left: 0rpx;
	}
	.biwan_img .item_video{
		width: 300rpx;
		height: 300rpx;
		display:inline-block;
		margin: 0 10rpx;
		color: #000000;
		background: #FFFFFF;
	}
	.biwan_img .item_video .image{
		
		height: 200rpx;
		overflow: hidden;
		margin: 0;
		border-radius: 20rpx;
	}
	.biwan_img .item_video .title{
		position: relative;
		
		font-size: 30rpx;
		font-weight: normal;
		line-height: 80rpx;
		margin: 0 20rpx;
		margin-top: 200rpx;
	}
	.biwan_img .item_video:first-child{
		
		margin-left: 0;
	}
	.biwan_img scroll-view{
		height: 300rpx;
		color: #FFFFFF;
	}
</style>
