<template>
	<view class="content">
		<view class="details-box">
			<view class="detail-tetel">分享</view>
			<view class="datail-time">
				<view> {{msglist.time}}</view>	
				<view class="datail-address-inc">
					<u-icon name="map-fill" color="#888888" size="48"></u-icon>
					<view class="datail-address">{{msglist.address}}</view>
				</view>
			</view>
			<view class="datail-desc">{{msglist.title}}</view>
			<view class="swiper" >
				<u-swiper :list="msglist.list" :height="674" :width="750" mode="number" indicator-pos="bottomRight" @click="details(index)"></u-swiper>
			</view>
			<view class="fabulous" @click="fabulous">
				<u-icon name="thumb-up" color="#fb8d44" size="88"></u-icon>
				<view>为文本点赞</view>
			</view>
			<view class="fabulous-per">
				<view class="per" v-if="index<=7" v-for="(item,index) in msglist.fabulous_per">
					<u-avatar :size="60" :src="item"></u-avatar>
				</view>
				<view class="">等人觉得很赞</view>
			</view>
		</view>
		<view class="comment">
			<view class="comment-list" v-for="(it,idx) in msglist.comment">
				<view class="comment-img">
					<u-avatar :size="60" :src="it.comment_img"></u-avatar>
					<view>{{it.comment_name}}</view>
				</view>
				<view class="comment-con">{{it.comment}}</view>
			</view>
		</view>
		<view class="bottom">
			<view class="bottom-int">
				<input placeholder="说点什么" :value="cot" adjust-position="false" @input="input" confirm-type="send" />
			</view>
			<view class="bottom-bt">
				<view class="bottom-bt-inc" @click="fasong">
					<image src="../../static/dongtai/fa.png" mode="" style="width:50rpx;height: 50rpx; "></image>
					<view>发送</view>
				</view>
				<view class="bottom-bt-inc" @click="fabulous">
					<u-icon v-if="hide==0" name="thumb-up"  color="#888888" size="58"></u-icon>
					<u-icon v-if="hide==1" name="thumb-up"  color="#fb8d44" size="58"></u-icon>
					<view>点赞</view>
				</view>
				<view class="bottom-bt-inc" @click="hides">
					<u-icon name="star" color="#888888" size="50" v-if="cang==0"></u-icon>
					<u-icon name="star" color="#fb8d44" size="50" v-if="cang==1"></u-icon>
					<view>收藏</view>
				</view>
				
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				cot:'',
				cang:0,
				hide:0,
				msglist: {
						nickname: "测试测试测试",
						src: "https://ewr1.vultrobjects.com/imgspice2/000/004/888/353_1a8_8d1.jpg",
						list: ['https://cdn.uviewui.com/uview/swiper/1.jpg',
								'https://cdn.uviewui.com/uview/swiper/2.jpg',
								'https://cdn.uviewui.com/uview/swiper/3.jpg'
							],
						address: "安徽黄山",
						title: "五一出游去山间看看吧 不会后悔的，没有人挤人，没有车挤车 找一家山间的美食民宿",
						count: 2000,
						time:"2021-05-29",
						fabulous_per:['https://ewr1.vultrobjects.com/imgspice2/000/004/888/353_1a8_8d1.jpg','https://ewr1.vultrobjects.com/imgspice2/000/004/888/353_1a8_8d1.jpg','https://ewr1.vultrobjects.com/imgspice2/000/004/888/353_1a8_8d1.jpg'],
						comment:[
							{
								comment_img:'https://ewr1.vultrobjects.com/imgspice2/000/004/888/353_1a8_8d1.jpg',
								comment_name:'月野兔',
								comment:'五一出游去山间看看吧 不会后悔的，没有人挤人，没有车挤车 找一家山间的美食民宿'
							},
							{
								comment_img:'https://ewr1.vultrobjects.com/imgspice2/000/004/888/353_1a8_8d1.jpg',
								comment_name:'月野兔',
								comment:'五一出游去山间看看吧 不会后悔的，没有人挤人，没有车挤车 找一家山间的美食民宿'
							},
							{
								comment_img:'https://ewr1.vultrobjects.com/imgspice2/000/004/888/353_1a8_8d1.jpg',
								comment_name:'月野兔',
								comment:'五一出游去山间看看吧 不会后悔的，没有人挤人，没有车挤车 找一家山间的美食民宿'
							}
						]
					},
					
					
			}
		},
		onLoad() {

		},
		methods: {
			//点赞
			fabulous(){
				
				if(this.hide==0){
					uni.showToast({
					    title: '很高兴你的点赞',
					    duration: 2000
					});
					let list = this.msglist;
					list.fabulous_per.splice(0,0,'https://ewr1.vultrobjects.com/imgspice2/000/004/888/353_1a8_8d1.jpg');
					this.msglist = list;
					
					this.hide = 1;
				}else{
					uni.showToast({
					    title: '你已点赞，无需再点',
					    duration: 2000,
						icon:'none'
					});
				}
				
			},
			//收藏
			hides(){
				if(this.cang==0){
					uni.showToast({
					    title: '收藏成功',
					    duration: 2000
					});
					this.cang = 1;
				}else{
					uni.showToast({
					    title: '你已收藏',
					    duration: 2000,
						icon:'none'
					});
				}
				
			},
			input:function(e){
				this.cot = e.detail.value
			},
			//评论
			fasong(e){
				let commentlist = {};
				let list = this.msglist;
				let value =this.cot; 
					commentlist.comment_img = 'https://ewr1.vultrobjects.com/imgspice2/000/004/888/353_1a8_8d1.jpg',
					commentlist.comment_name = '月野兔',
					commentlist.comment = value
				list.comment.splice(0,0,commentlist);
				
				this.comment = list;
				this.cot = '';
			}
		}
	}
</script>

<style>
	page{
		background: #f6f6f6;
	}
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	.details-box{
		background: #FFFFFF;
		width: 100%;
		padding: 40rpx 32rpx;
		margin-bottom: 20rpx;
	}
	.detail-tetel{
		font-size: 32rpx;
		color: #464646;
	}
	.datail-time{
		margin-top: 10rpx;
		font-size: 24rpx;
		color: #9c9c9c;
		display: flex;
		flex-direction: row;
		justify-content: flex-start;
		align-items: flex-end;
	}
	.datail-address-inc{
		display: flex;
		flex-direction: row;
		align-items: flex-end;
		margin-left: 10rpx;
	}
	.datail-address{
		margin-left: 10rpx;
		font-size: 28rpx;
	}
	.datail-desc{
		margin-top: 20rpx;
		font-size: 32rpx;
		display: flex;
		flex-direction: row;
	}
	.swiper {
		width: 100%;
		height: 672rpx;
		margin-top: 15px;
	}
	.fabulous{
		margin-top: 50rpx;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}
	.fabulous>view{
		color: #fb8d44;
		font-size: 28rpx;
	}
	.fabulous-per{
		margin-top: 20rpx;
		display: flex;
		flex-direction: row;
		justify-content: flex-start;
		align-items: center;
		width: 100%;
		overflow: hidden;
		white-space:normal;
		word-break:break-all
	}
	.fabulous-per>view{
		font-size: 28rpx;
		color: #a7a7a7;
	}
	.per{
		float: left;
		/* width: 50rpx;
		height: 50rpx; */
		border-radius: 50%;
		margin-right: 15rpx;
	}
	.comment{
		margin-top: 10rpx;
		width: 100%;
		background: #FFFFFF;
		padding: 0rpx 32rpx;
		margin-bottom: 100rpx;
	}
	.comment-list{
		margin:20rpx 0rpx ;
		border-bottom: 1rpx solid #ddd;
	}
	.comment-img{
		width: 100%;
		/* height: 80rpx; */
		display: flex;
		flex-direction: row;
		justify-content: flex-start;
		align-items: center;
	}
	.comment-img>view{
		margin-left: 10rpx;
		font-size: 28rpx;
		font-weight: bold;
	}
	.comment-con{
		padding-left:80rpx ;
		margin: 20rpx 0rpx;
		font-size: 28rpx;
	}
	.bottom{
		position: fixed;
		bottom: 0rpx;
		left: 0rpx;
		background: #FFFFFF;
		-webkit-box-shadow: 0px 0px 10px rgba(0,0,0,.8);
		  -moz-box-shadow: 0px 0px 10px rgba(0,0,0,.8);
		  box-shadow: 0px 0px 10px rgba(0,0,0,.8);
		z-index: 2;
		height: 120rpx;
		width: 100%;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		padding: 0rpx 32rpx;
	}
	.bottom-int{
		width: 45%;
		height: 80rpx;
		background: #e8e8e8;
		border-radius: 50rpx;
	}
	.bottom-int>input{
		width: 100%;
		height: 80rpx;
		line-height: 80rpx;
		padding-left: 20rpx;
		font-size: 28rpx;
	}
	.bottom-bt{
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		width: 55%;
	}
	.bottom-bt-inc{
	/* 	width: 33.3%; */
		height: 100%;
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
	}
	.bottom-bt-inc>view{
		font-size: 28rpx;
		margin-left: 10rpx;
	}
</style>
