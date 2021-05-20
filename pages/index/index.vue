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
					<view class="item_list" @tap="path(item.path)">
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
				<view class="yuyue" @click="formulate">
					<view class="goupiao_con">
						<view class="title">导游预约</view>
						<view class="miaosu">轻松了解民俗文化</view>
					</view>
					<image class="icon" src="../../static/home/daoyou.png" mode="widthFix"></image>
				</view>
			</view>
			<!-- 景区介绍 -->
			<view class="qujs">
				<view class="qujs_item gengduo_more" >
					<view>
						<text>导览地址：</text> 贵州省铜仁市石阡县
					</view>
					<image class="gengduo" src="../../static/home/dingwei.png" mode="widthFix" style="width: 35rpx;"></image>
				</view>
			</view>
		</view>
		<!-- 精彩楼层 -->
		<view class="video">
			<view class="video-top">
				<view class="video-tel">精彩视频</view>
				<view class="inc">
					<view>更多</view>
					<u-icon  size="30" name="arrow-right"></u-icon>
				</view>
			</view>
			<view class="swiper">
				<scroll-view class="scroll-view" scroll-x="true" @scroll="scroll" scroll-left="120">
					<view class="scroll-view-con" v-for="(item,index) in videolist">
						<image :src="item" class="video-img"></image>
						<image src="../../static/home/baofang.png" class="bf"></image>
					</view>
					
				</scroll-view>
			</view>
		</view>
		<!-- 楼层 -->
		<view class="floor" v-for="(item,index) in  floorlist" >
			<view class="floor-top" :style="{background: 'linear-gradient('+item.background_color[0]+','+item.background_color[1]+')'}">
				<view class="floor-top-tel">
					<view>{{item.title}}</view>
					<view style="font-size: 28rpx; color:#666666">{{item.describe}}</view>
				</view>
				<view class="floor-top-img">
					<image :src="item.background_img" mode="aspectFit"></image>
				</view>
			</view>
			<view class="floor-zj">
				<view class="floor-zj-tag"  v-for="(items,idx) in item.tags">{{items}}</view>
			</view>
			<view class="floor-bottom" >
				<view class="floor-bottom-tag" v-for="(it,idex) in item.content">
					<image :src="it.img" mode="scaleToFill"></image>
					<view>{{it.describe}}</view>
				</view>
			</view>
		</view>
		
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				scrollTop: 0,
				old: {
					scrollTop: 0
				},
				videolist:['../../static/home/bg2.png','../../static/home/bg3.png','../../static/home/bg1.png'],
				list:[
					{
						img:'../../static/home/lvyougonglv.png',
						title:'路由攻略'
					},{
						path: "/pages/product/index",
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
					},{
						img:'../../static/home/zhiyuanzhe.png',
						title:'志愿者',
						path:'/pages/volunteer/index'
					}
				],
				floorlist:[
					{
						title:"生态教育",
						describe:"旅行教育，边玩边学",
						background_img:"../../static/home/jiaoyu.png",
						background_color:['#FCA67B','#FFFCFA'],
						tags:['研学旅行','研学旅行','研学旅行','研学旅行','研学旅行','研学旅行'],
						content:[
							{
								img:"../../static/home/bg1.png",
								describe:'中小学生研学,中小学生研学...'
							},
							{
								img:"../../static/home/bg1.png",
								describe:'中小学生研学,中小学生研学...'
							},
							{
								img:"../../static/home/bg1.png",
								describe:'中小学生研学,中小学生研学...'
							}
						]
					},
					{
						title:"森林康养",
						describe:"旅行教育，边玩边学",
						background_img:"../../static/home/jiankang.png",
						background_color:['#F9EDAA','#FFFCFA'],
						tags:['天然氧吧','天然氧吧','天然氧吧','天然氧吧','天然氧吧','天然氧吧'],
						content:[
							{
								img:"../../static/home/bg3.png",
								describe:'天然氧吧,天然氧吧...'
							},
							{
								img:"../../static/home/bg3.png",
								describe:'天然氧吧,天然氧吧...'
							},
							{
								img:"../../static/home/bg3.png",
								describe:'天然氧吧,天然氧吧...'
							}
						]
					},
					{
						title:"户外活动",
						describe:"旅行教育，边玩边学",
						background_img:"../../static/home/huodong.png",
						background_color:['#8AE6E4','#FFFCFA'],
						tags:['汽车露营','汽车露营','汽车露营','汽车露营','汽车露营','汽车露营'],
						content:[
							{
								img:"../../static/home/bg2.png",
								describe:'佛顶山汽车露营,佛顶山汽车露营...'
							},
							{
								img:"../../static/home/bg2.png",
								describe:'佛顶山汽车露营,佛顶山汽车露营...'
							},
							{
								img:"../../static/home/bg2.png",
								describe:'佛顶山汽车露营,佛顶山汽车露营...'
							}
						]
					},
					{
						title:"文化体验",
						describe:"旅行教育，边玩边学",
						background_img:"../../static/home/tiyan.png",
						background_color:['#F8BBB8','#FFFCFA'],
						tags:['篝火晚会','篝火晚会','篝火晚会','篝火晚会','篝火晚会','篝火晚会'],
						content:[
							{
								img:"../../static/home/bg2.png",
								describe:'篝火晚会,篝火晚会...'
							},
							{
								img:"../../static/home/bg2.png",
								describe:'篝火晚会,篝火晚会...'
							},
							{
								img:"../../static/home/bg2.png",
								describe:'篝火晚会,篝火晚会...'
							}
						]
					}
				]
			}
		},
		onLoad() {

		},
		methods: {
			//导航跳转
			path:function(e){
				let url = e;
				console.log(url)
				uni.navigateTo({
					url:"url"
				})
			},
			// 精彩视频滑动
			scroll: function(e) {
				this.old.scrollTop = e.detail.scrollTop
			},
			//跳转定制游
			formulate:function(e){
				uni.navigateTo({
					url:"/pages/formulate/index"
				})
			}
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
		margin-bottom: 50rpx;
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
		padding-bottom: 10rpx;
	}
	.gengduo{
		width: 10rpx;
		float: right;
		margin: 0 50rpx;
	}
	/* 精彩视频 */
	.video{
		margin: 30rpx;
	}
	.video-top{
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
	}
	.video-tel{
		border-left:6rpx solid #07C160 ;
		padding-left: 20rpx;
		font-size: 36rpx;
		font-weight: bold;
	}
	.inc{
		display: flex;
		flex-direction: row;
	}
	.inc>view{
		font-size: 28rpx;
		color: #07C160;
		margin-right: 10rpx;
	}
	.scroll-view{
		width: 100%;
		height: 300rpx;
		margin-top: 30rpx;
		white-space: nowrap;
		
	}
	.scroll-view-con{
		display: inline-block;
		height: 100%;
		width: 80%;
		margin-left: 30rpx;
		background: #000000;
		border-radius: 25rpx;
		padding: 20rpx 0rpx;
		position: relative;
	}
	.video-img{
		width: 100%;
		height: 100%;
		
	}
	.bf{
		display: inline-block;
		position: relative;
		top: -80rpx;
		left: -55%;
		width: 100rpx;
		height: 100rpx;
		z-index: 1;
		/* opacity: 0.5; */
	}
	/* 楼层（） */
	.floor{
		margin: 30rpx;
		background: #ffffff;
		border-radius: 20rpx;
		padding-bottom: 20rpx;
		display: flex;
		flex-direction: column;
	}
	.floor-top{
		width: 100%;
		height: 200rpx;
		border-radius: 10rpx 10rpx 0rpx 0rpx;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		padding: 0rpx 30rpx;
		
		
	}
	.floor-top-tel>view{
		font-size: 30rpx;
		font-weight: bold;
		margin-top: 15rpx;
	}
	.floor-top-img{
		width: 180rpx;
		height: 180rpx;
		
	}
	.floor-top-img>image{
		width: 100%;
		height: 100%;
	}
	.floor-zj{
		margin-top: 10rpx;
		padding:20rpx 32rpx;
	}
	.floor-zj-tag{
		float: left;
		width: 30%; 
		height: 60rpx;
		line-height: 60rpx;
		background: #F7F8FC;
		font-size: 30rpx;
		color: #666666;
		margin-left: 3%;
		margin-top: 20rpx;
		text-align: center;
		font-size: 30rpx;
	}
	.floor-bottom{
		padding:20rpx 32rpx;
	}
	.floor-bottom-tag{
		float: left;
		width: 30%;
		margin-left: 3%;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		
	}
	.floor-bottom-tag>view{
		width: 100%;
		display: -webkit-box;
		-webkit-box-orient: vertical;
		-webkit-line-clamp: 1;
		overflow: hidden;
		margin-top: 10rpx;
		font-size: 28rpx;
		color: #464646;
		
	}
	.floor-bottom-tag>image{
		width: 100%;
		border-radius: 15rpx;
		height: 150rpx;
	}
/* 	.floor-top:first-of-type{
		background-image: linear-gradient(#FCA67B,#FFFCFA);
	}
	.floor-top:nth-last-of-type(1){
		background-image: linear-gradient(#F9EDAA,#FFFCFA);
	} */
</style>
