<template>
	<view class="content">
		<!-- 搜索 -->
		<view class="search">
			<view class="search-box">
				<input  placeholder ="搜索" />
				<image src="../../static/home/sousuo.png"></image>
			</view>
			<view class="search-inc" @click="shows">
				<view>筛选</view>
				<image src="../../static/home/saixuan.png" ></image>
			</view>
		</view>
		<!-- 排序 -->
		<view class="sort">
			<view class="sort-ul" @click="change(0)" :class="[btnnum==0?'active':'']">综合</view>
			<view class="sort-ul" @click="change(1)" :class="[btnnum==1?'active':'']">销量</view>
			<view class="sort-ul" @click="change(2)" :class="[btnnum==2?'active':'']">
				<view>价格</view>
				<view class="sort-ul-sort">
					<u-icon size="18" name="arrow-up-fill" color="#000000"></u-icon>
					<u-icon size="18" name="arrow-down-fill" color="#000000"></u-icon>
				</view>
			</view>
		</view>
		<!-- 商品列表 -->
		<view class="goods-box">
			<view class="list" v-for="(item,index) in list" @click="details">
				<image :src="item.goods_img" mode="scaleToFill"></image>
				<view class="list-name">
					<view>{{item.goods_name}}</view>
					<view style="color: #FF0000;font-weight: bold;">{{item.goods_money}}</view>
				</view>
			</view>
		</view>
		<!-- 没有更多 -->
		<view class="null">没有更多了~</view>
		<!-- 赛选侧边弹出层 -->
		<u-popup v-model="show" mode="right" width="50%">
			<view class="popup-ul" v-for="(it,idx) in choose">
				{{it}}
			</view>
		</u-popup>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello',
				btnnum:0,
				show:false,
				list:[
					{
						goods_img:"https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg.yzcdn.cn%2Fupload_files%2F2015%2F05%2F18%2FFkpm67LDL8t0CXanGIyn5L9vaCcw.jpg%3FimageView2%2F2%2Fw%2F580%2Fh%2F580%2Fq%2F75%2Fformat%2Fjpg&refer=http%3A%2F%2Fimg.yzcdn.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1624001293&t=cd57513a819f22a9b626274984d6091a",
						goods_name:"威宁荞酥",
						goods_money:30.5
					},
					{
						goods_img:"https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fg-search1.alicdn.com%2Fimg%2Fbao%2Fuploaded%2Fi4%2F318649248%2FTB2IBdzcpXXXXXtXXXXXXXXXXXX_%21%21318649248.jpg_300x300.jpg&refer=http%3A%2F%2Fg-search1.alicdn.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1624001458&t=98e36f6415f5bd12d9b93995ba735d72",
						goods_name:"威宁荞茶",
						goods_money:30.5
					},
					{
						goods_img:"https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg.alicdn.com%2Ftfscom%2Fi1%2F1715445650%2FTB2Tj5GXa4441JjSZFsXXcB8pXa_%21%211715445650.jpg&refer=http%3A%2F%2Fimg.alicdn.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1624001549&t=17dfc716c32397ee1d2f16d5c6bfd3af",
						goods_name:"威宁小粑粑",
						goods_money:30.5
					},{
						goods_img:"https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg.yzcdn.cn%2Fupload_files%2F2015%2F05%2F18%2FFkpm67LDL8t0CXanGIyn5L9vaCcw.jpg%3FimageView2%2F2%2Fw%2F580%2Fh%2F580%2Fq%2F75%2Fformat%2Fjpg&refer=http%3A%2F%2Fimg.yzcdn.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1624001293&t=cd57513a819f22a9b626274984d6091a",
						goods_name:"威宁荞酥",
						goods_money:30.5
					},
				],
				choose:['包邮','包邮包邮','包邮']
			}
		},
		onLoad() {

		},
		methods: {
			//切换排序
			change:function(e){
				this.btnnum=e;
			},
			//赛选侧边弹出层
			shows:function(e){
				this.show=true
			},
			//跳转详情
			details:function(e){
				uni.navigateTo({
					url:"/pages/product/details"
				})
			}
		}
	}
</script>

<style>
	page{
		background: #F2F5FA;
	}
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	/* 搜索 */
	.search{
		position: fixed;
		top:44px;
		left: 0;
		height: 120rpx;
		width: 100%;
		/* background:#FFF7CC ; */
		padding: 20rpx 32rpx;
		display: flex;
		flex-direction: row;
	}
	.search-box{
		width: 550rpx;
		height: 100%;
		background: #FFFFFF;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
	}
	.search-box>input{
		width: 100%;
		height: 100%;
		text-align: center;
		font-size: 30rpx;
	}
	.search-box>image{
		position: relative;
		top: -5rpx;
		right: 20rpx;
		width: 45rpx;
		height: 45rpx;
		
	}
	.search-inc{
		width: 200rpx;
		height: 100%;
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
	}
	.search-inc>image{
		width: 40rpx;
		height: 40rpx;
	}
	.search-inc>view{
		margin-right: 25rpx;
		font-size: 32rpx;
		color: #007AFF;
	}
	/* 排序 */
	.sort{
		background: #FFFFFF;
		height: 120rpx;
		width: 100%;
		margin-top: 120rpx;
		padding: 0rpx 32rpx;
	}
	.sort-ul{
		float: left;
		width: 33.3%;
		line-height: 118rpx;
		text-align: center;
		font-size: 34rpx;
		font-weight: 100;
		color: #555555;
		/* display: flex;
		flex-direction: row; */
	}
	.active{
		color: #FF0000;
	}
	.sort-ul-sort{
		position: relative;
		top: -80rpx;
		left: 50rpx;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		margin-left: 8rpx;
	}
	/* 商品列表 */
	.goods-box{
		padding: 0rpx 32rpx;
		width: 100%;
	}
	.list{
		float: left;
		width: 320rpx;
		margin-left: 12rpx;
		margin-right: 10rpx;
		margin-top: 20rpx;
		background: #FFFFFF;
		border-radius: 25rpx;
		display: flex;
		flex-direction: column;
		/* justify-content: space-between;
		align-items:center ; */
	}
	.list>image{
		width: 100%;
		height: 350rpx;
		border-radius: 25rpx 25rpx 0 0;
	}
	.list-name{
		padding: 20rpx 15rpx;
		/* margin-top: 10rpx; */
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: flex-start;
	}
	.list-name>view{
		font-size: 30rpx;
	}
	.null{
		width: 100%;
		text-align: center;
		margin-top: 30rpx;
		font-size: 32rpx;
		color: #575757;
	}
	/* 赛选侧边弹出层 */
	.popup-ul{
		height:50rpx;
		font-size: 28rpx;
		line-height: 50rpx;
		background: #F2F5FA;
		float: left;
		padding: 2rpx 20rpx;
		margin-left: 20rpx;
		margin-top: 30rpx;
		text-align: center;
	}
</style>
