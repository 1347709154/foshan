<template>
	<view class="content">
		<!-- 轮播图 -->
		<view class="wrap">
			<u-swiper :list="goods.goods_imgs" height="350"></u-swiper>
		</view>
		<!-- 商品信息 -->
		<view class="goods-box">
			<view class="goods-mun">
				<view class="goods-mun-te">限时秒杀</view>
				<view class="u-count-down">
					<text>距结束</text>
					<u-count-down :timestamp="86400" hide-zero-day="false" separator-color="#FFE9E8" separator-size="40" bg-color="#FFE9E8" color="#FF2222"></u-count-down>
				</view>
			</view>
			<view class="goods-name">
				<view class="name">{{goods.goods_name}}</view>
				<view class="fenxiang">
					<u-icon name="share"  size="38" color="#ffffff" style="margin-left: 10rpx;"></u-icon>
					<text>分享</text>
				</view>
			</view>
			<view class="goods-piece">
				<view class="mun">
					<view class="mun-x">¥{{goods.price_x}}</view>
					<view class="mun-y">¥{{goods.price_y}}</view>
				</view>
				<view class="tui">已抢:{{goods.sold}}件</view>
			</view>
		</view>
		<!-- 导航栏 -->
		<view class="nav">
			<view @click="change(1)" class="nav-ul"><text :class="[btnnum==1?'actives':'text']">商品详情</text></view>
			<view @click="change(2)" class="nav-ul"><text :class="[btnnum==2?'actives':'text']">评论</text></view>
			
		</view>
		<!-- 商品评价 -->
		<view class="evaluate" v-if="btnnum==2">
			<view class="evaluate-tel">
				<view class="evaluate-tel-pj">商品评价（99）</view>
				<view class="gengduo">
					<view>查看全部</view>
					<u-icon name="arrow-right" color="#9F9F9F" size="28"></u-icon>
				</view>
			</view>
			<view class="evaluate-list" v-for="(it,inx) in evaluatelist">
				<view class="list-img">
					<image :src="it.user_img"></image>
					<view class="list-img-name">
						<view class="na" style="margin-bottom: 10rpx;">
							<view style="text-align: left;">{{it.user_name}}</view>
							 <view class="list-img-tmie">{{it.tmie}}</view>
						</view>
						<view>
							<!-- <u-rate  :v-model="it.value"  inactive-color="#FA3534" gutter="10" :disabled="true"  inactive-icon="heart-fill"></u-rate> -->
						</view>
						
					</view>
					
				</view>
				<view class="list-content">
					<view class="list-content-tel">{{it.content}}</view>
					<view class="list-content-img">
						<image :src="img" v-for="(img,idv) in it.img" mode="aspectFill"></image>
					</view>
				</view>
			</view>
		</view>
		<!-- 商品详情 -->
		<view class="goods-details" v-if="btnnum==1">
			<!-- <view class="details">商品详情</view> -->
			<view class="richtext">
				<u-parse :html="richtext"></u-parse>
			</view>
		</view>
		<!-- 底部按钮 -->
		<view class="bottom">
			<view class="bottom-l">
				<view class="bottom-x">
					<view>
						<u-icon name="home" color="#9F9F9F" size="45"></u-icon>
						<view>店铺</view>
					</view>
					<view>
						<u-icon name="chat" color="#9F9F9F" size="48"></u-icon>
						<view>客服</view>
					</view>
				</view>
			</view>
			<view class="bottom-r" @click="show1">
				<view class="yy">
					<view>立即购买</view>
				</view>
			</view>
		</view>
		
		<!-- 底部弹窗 -->
		<u-popup v-model="show" mode="bottom"  closeable='true'>
			<view class="popup-tel">选择规格</view>
			<view class="popup-goods">
				<view class="popup-img">
					<image mode="aspectFill" :src="goods.goods_img"></image>
				</view>
				<view class="popup-name">
					<view style="font-weight: bold;">{{goods.goods_name}}</view>
					<view style="color: #999999;">库存：{{goods.stock}}</view>
					<view style="color: #E01212;">包邮</view>
					<view style="color: #E01212;"> ￥{{goods.price_x}} <text>￥{{goods.price_y}}</text></view>
				</view>
			</view>
			<view class="norms">选择规格</view>
			<view class="norms-box">
				<view class="norms-box-ul" :class="[isactive==nix?'active':'']" v-for="(norms,nix) in goods.norms" @click="norm(nix)">{{norms}}</view>
			</view>
			<view class="purchase">
				<view class="purchase-num">
					<view class="purchase-num-te">购买数量</view>
						<u-number-box v-model="purchase" @change="valChange"></u-number-box>
				</view>
			</view>
			<view class="Submit" @click="Submit">确定</view>
		</u-popup>
		
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				show:false,//底部弹窗
				btnnum:1,
				isactive :'',//规格选择
				purchase:1,//选择数量
				
				goods:{
					"price_x":"29.00",
					"price_y":"59.00",
					"goods_name":"猕猴桃新鲜水果绿色原产地，产自 凉都六盘水依山傍水农家肥现摘现发",
					"sold":1025,
					"norms":['15个装','25个装','35个装'],
					"goods_imgs":['https://cdn.uviewui.com/uview/swiper/1.jpg','https://cdn.uviewui.com/uview/swiper/2.jpg','https://cdn.uviewui.com/uview/swiper/3.jpg'],
					"goods_img":"https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fdpic.tiankong.com%2Fka%2Fua%2FQJ8597345361.jpg%3Fx-oss-process%3Dstyle%2Fshows&refer=http%3A%2F%2Fdpic.tiankong.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1624435987&t=1a049e06d00a67b516d2a7539eecc3b0",
					"stock":1256
				},
				evaluatelist:[
					{
						user_img:'../../static/user/user_img-1.png',
						user_name:'张三',
						tmie:'2019-11-24',
						value:4,
						content:'满意，环境优美，设施齐全，各方面都非常好',
						img:['https://cdn.uviewui.com/uview/swiper/1.jpg','https://cdn.uviewui.com/uview/swiper/2.jpg','https://cdn.uviewui.com/uview/swiper/3.jpg']
					},{
						user_img:'../../static/user/user_img-1.png',
						user_name:'张三',
						tmie:'2019-11-24',
						value:2,
						content:'满意，环境优美，设施齐全，各方面都非常好',
						img:['https://cdn.uviewui.com/uview/swiper/1.jpg','https://cdn.uviewui.com/uview/swiper/2.jpg','https://cdn.uviewui.com/uview/swiper/3.jpg']
					}
				],
				richtext:`
					<p class="photo_img_20190808" style="text-align: center;"><img src="https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fdpic.tiankong.com%2Fka%2Fua%2FQJ8597345361.jpg%3Fx-oss-process%3Dstyle%2Fshows&refer=http%3A%2F%2Fdpic.tiankong.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1624435987&t=1a049e06d00a67b516d2a7539eecc3b0"  isflag="1"></p>
					<p class="photo_img_20190808" style="text-align: center;"><img src="https://gimg2.baidu.com/image_search/src=http%3A%2F%2Ftemp3.jinnong.cn%2Fimage%2F20150921%2F20150921082131863186.jpg&refer=http%3A%2F%2Ftemp3.jinnong.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1624436410&t=4e4fe9b76b1d1d55d9c594bc12254600"  isflag="1"></p>
				`
			}
		},
		onLoad() {

		},
		methods: {
			//底部弹窗
			show1:function(){
				this.pin = false,
				this.show = true;
			},
			//选择规格
			norm:function(e){
				this.isactive =e
			},
			//数量加减
			valChange(e) {
				this.purchase = e.value
			},
			// 导航切换
			change(e) {
				this.btnnum = e
				 console.log(this.btnnum)
			},
			Submit:function(){
				
			}
		}
	}
</script>

<style lang="scss">
	page{
		background: #F4F4F4;
	}
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	/* 轮播图 */
	.wrap {
		height: 350rpx;
		width: 100%;
	}
	/* 商品信息 */
	.goods-box{
		display: flex;
		flex-direction: column;
		padding-bottom: 30rpx;
		width: 100%;
		background: #F4F4F4;
		
	}
	.goods-mun{
		background:linear-gradient(to right, #FF2F61,#FF6247);
		width: 100%;
		height: 100rpx;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		padding: 0rpx 32rpx;
	}
	.mun{
		display: flex;
		flex-direction: row;
		justify-content:center;
		align-items: flex-end;
		color: #FE343F;
	}
	.goods-mun-te{
		font-size: 40rpx;
		font-weight: bold;
		margin-right: 10rpx;
		color: #FFFFFF;
	}
	.mun-x{
		font-size: 34rpx;
		font-weight: bold;
		margin-right: 10rpx;
	}
	.mun-y{
			font-size: 26rpx;
			text-decoration:line-through
	}
	.u-count-down{
		color: #FFEAE9;
		font-size: 32rpx;
	}
	.u-count-down>text{
		margin-right: 10rpx;
	}
	.u-countdown-ite{
		padding: 10rpx;
	}
	.goods-name{
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		padding-left:32rpx ;
		margin-top: 30rpx;
		position: relative;
	}
	.name{
		font-size: 32rpx;
		font-weight: bold;
		width: 80%;
	}
	.fenxiang{
		width: 120rpx;
		height: 60rpx;
		position: relative;
		right: 0rpx;
		top: 0rpx;
		background: #FD587E;
		display: flex;
		flex-direction: row;
		justify-items: center;
		align-items: center;
		border-radius: 35rpx 0rpx 0rpx 35rpx;
	}
	.fenxiang>text{
		font-size: 28rpx;
		color: #FFFFFF;
		margin-left: 5rpx;
	}
	.goods-piece{
		padding: 0rpx 32rpx;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		margin-top: 40rpx;
	}
	.piece{
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
	}
	.tui{
		color: #FF2628;
		font-size: 28rpx;
	}
	.piece-pre{
		width: 140rpx;
		height: 50rpx;
		line-height: 50rpx;
		text-align: center;
		border: 1rpx solid #FF2628;
		border-radius: 15rpx;
		font-size: 24rpx;
		color: #FF2628;
	}
	.piece-mun{
		font-size: 24rpx;
		color: #ff2628;
		margin-left: 15rpx;
		height: 50rpx;
		line-height: 50rpx;
	}
	/* 导航栏 */
	.nav{
		height: 100rpx;
		width: 100%;
		background: #ffffff;
		margin-bottom: 20rpx;
	}
	.nav-ul{
		float: left;
		width: 50%;
		height: 100rpx;
		text-align: center;
	}
	.nav-ul>.text{
		display: inline-block;
		height: 100rpx;
		font-size: 32rpx;
		font-weight: bold;
		line-height: 100rpx;
	}
	.actives{
		display: inline-block;
		font-size: 32rpx;
		height: 96rpx;
		line-height: 98rpx;
		color: #FE343F;
		font-weight: bold;
		border-bottom: 4rpx solid #FE343F;
	}
	/* 商品评价 */
	.evaluate{
		background: #FFFFFF;
		width: 100%;
		// margin-bottom: 30rpx;
		padding: 0rpx 32rpx;
		padding-bottom: 20rpx;
		margin-bottom: 120rpx;
	}
	.evaluate-tel{
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		
	}
	.gengduo{
		display: flex;
		flex-direction: row;
		justify-content: flex-end;
		align-items: center;
		color: #666666;
		font-size: 26rpx;
	}
	.gengduo>view{
		margin-right: 10rpx;
	}
	.evaluate-tel{
		margin-top: 30rpx;
	}
	.evaluate-tel-pj{
		font-size: 32rpx;
	}
	.evaluate-list{
		width: 100%;
		margin-top: 40rpx;
	}
	.list-img{
		display: flex;
		flex-direction: row;
		// align-items: center;
	}
	.list-img>image{
		width: 120rpx;
		height: 120rpx;
		border-radius: 50%;
	}
	.list-img-name{
		margin-left: 15rpx;
		display: flex;
		flex-direction: column;
		
		margin-top: 25rpx;
		font-size: 28rpx;
	}
	.list-img-name>.na{
		display: flex;
		flex-direction: row;
		justify-content: flex-start;
		align-items: center;
	}
	.list-img-tmie{
		margin-left: 20rpx;
		font-size: 28rpx;
	}
	.list-content{
		width: 100%;
		margin-top: 20rpx;
	}
	.list-content-tel{
		font-size: 28rpx;
	}
	.list-content-img{
		display: flex;
		flex-direction: row;
		justify-content: flex-start;
		align-items: center;
		margin-top: 10rpx;
	}
	.list-content-img>image{
		float: left;
		width: 160rpx;
		height: 160rpx;
		margin-right:20rpx ;
	}
	/* 商品详情 */
	.goods-details{
		width: 100%;
		min-height:350rpx ;
		background: #FFFFFF;
		margin-bottom: 120rpx;
	}
	.details{
		margin-top: 30rpx;
		padding-left: 32rpx;
		font-size: 30rpx;
		font-weight: bold;
	}
	.richtext{
		min-height: 500rpx;
		height: auto;
		width: 100%;
		margin: auto;
		margin-top: 27rpx
	}
	/* 底部按钮 */
	/* 底部按钮 */
	.bottom{
		width: 100%;
		height: 100rpx;
		position: fixed;
		bottom: 0rpx;
		left: 0rpx;
		/* background: #007AFF; */
		background: #FFFFFF;
		z-index: 2;
		-webkit-box-shadow: 0px 0px 10px rgba(0,0,0,.8);
		  -moz-box-shadow: 0px 0px 10px rgba(0,0,0,.8);
		  box-shadow: 0px 0px 10px rgba(0,0,0,.8);
		  display: flex;
		  flex-direction: row;
	}
	.bottom-l{
		display: flex;
		flex-direction: row;
	}
	.bottom-x{
		display: flex;
		flex-direction: row;
		
	}
	.bottom-x>view{
		width: 120rpx;
		height: 100rpx;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}
	.bottom-x>view>image{
		width: 50rpx;
		height: 50rpx;
	}
	.bottom-r{
		width: 630rpx;
		height: 100rpx;
		display: flex;
		flex-direction: row;
		justify-content: flex-end;
		align-items: center;
	}
	.yy{
		width: 100%;
		height: 100rpx;
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
		background: #E50505;
		color: #FFFFFF;
		font-size: 32rpx;
	}
	/* 底部弹窗 */
	.popup-tel{
		width: 100%;
		margin-top: 30rpx;
		font-size: 30rpx;
		text-align: center;
	}
	.popup-goods{
		margin-top: 30rpx;
		padding: 0rpx 32rpx;
		display: flex;
		flex-direction: row;
	}
	.popup-img{
		width: 220rpx;
		height: 200rpx;
	}
	.popup-img>image{
		width: 100%;
		height: 100%;
	}
	.popup-name{
		width: 480rpx;
		height: 200rpx;
		margin-left: 20rpx;
	}
	.popup-name>view{
		margin-bottom: 15rpx;
		font-size: 28rpx;
	}
	.popup-name>view>text{
		font-size: 24rpx;
		color: #666666;
		text-decoration:line-through;
		margin-left: 20rpx;
	}
	.norms{
		margin-top: 30rpx;
		text-align: left;
		font-size: 30rpx;
		padding: 0rpx 32rpx;
		font-weight: bold;
	}
	.norms-box{
		width: 100%;
		padding: 0rpx 32rpx;
		margin-top: 10rpx;
		display: flex;
		flex-direction: row;
	}
	.norms-box-ul{
		border: 1rpx solid #666666;
		float: left;
		margin-right: 20rpx;
		width: 200rpx;
		height: 60rpx;
		text-align: center;
		line-height: 60rpx;
		font-size: 28rpx;
	}
	.active{
		border: 0rpx solid #FFFFFF;
		background: #FF2F61;
		color: #FFFFFF;
	}
	.purchase{
		width: 100%;
		height: 120rpx;
		margin-top: 40rpx;
		padding: 0rpx 32rpx;
	}
	.purchase-num{
		width: 100%;
		height: 100%;
		border-bottom: 1rpx solid #ddd;
		border-top:1rpx solid #ddd ;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
	}
	.purchase-num-te{
		font-size: 30rpx;
		font-weight: bold;
	}
	.purchase-bt{
		display: flex;
		flex-direction: row;
		width: 250rpx;
		height: 60rpx;
		border: 1rpx solid #AEAEAE;
	}
	.Submit{
		height: 80rpx;
		width: 80%;
		margin-left: 10%;
		background:linear-gradient(to right, #FF6247,#FF2F61);
		text-align: center;
		line-height: 80rpx;
		margin-top: 40rpx;
		font-size: 30rpx;
		color: #FFFFFF;
		border-radius: 40rpx;
		margin-bottom: 20rpx;
	}
</style>
