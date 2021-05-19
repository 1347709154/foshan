<template>
	<view class="content">
		<view class="imgbox">
			<image src="https://ss0.bdstatic.com/70cFuHSh_Q1YnxGkpoWK1HF6hhy/it/u=2478350582,3338695212&fm=26&gp=0.jpg" mode=""></image>
		</view>
		<view class="titlebox">
			<view class="left title">
				<p>打卡当地民俗特色 体味别 样风情</p>
			</view>
			<view class="btnbox right">
				<view class="col left">
					<!-- 需要判断是否已收藏 -->
					<image src="../../static/food/col.png" mode=""></image>
					<p>收藏</p>
				</view>
				<view class="right share">
					<image src="../../static/food/share.png" mode=""></image>
					<p>分享</p>
				</view>
			</view>
		</view>
		<view class="richtextbox">
			<u-parse :html="richtext"></u-parse>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				richtext:`
					<p>　　巴尼小镇是云南省怒江傈僳族自治州首个易地扶贫搬迁集中安置点。从山上的金满村搬迁到巴尼小镇，近3年的时间里，搬迁户们的生活发生了可喜的变化。</p>
					<p class="photo_img_20190808" style="text-align: center;"><img src="//p2.img.cctvpic.com/photoworkspace/contentimg/2020/07/16/2020071613380766481.jpg" alt="泸水市巴尼小镇易地扶贫搬迁安置点全景 李韩金摄（人民视觉）" isflag="1"></p>
					<p>　　搬出四面透风、容易漏雨的“千脚落地房”，住进如今宽敞明亮的楼房，当地居民的生活不断改善。另一边，留在山上的村民在企业帮助下改种经济林果，家庭收入节节攀升。</p>
					<p class="photo_img_20190808" style="text-align: center;"><img src="//p3.img.cctvpic.com/photoworkspace/contentimg/2020/07/16/2020071613382671669.jpg" alt="金满村搬迁户在巴尼小镇的扶贫车间里上班 余秀英摄（人民视觉）" isflag="1"></p>
					<p>　　这阵子，52岁的米四东心里老惦记个事：吃两碗包谷稀饭。包谷稀饭是把包谷和蚕豆混在一起，有时加点腊肉，搁在三脚架上，生火煮制而成。在高黎贡山上，包谷稀饭曾是金满村人的主食，大多数人连个菜都不舍得炒，就配一碗蘸水吃。从山上搬下来快3年了，米四东说：“在山上盼着吃大米饭，如今天天吃米饭，又想念包谷稀饭了。”</p>
					<p>　　米四东的家在巴尼小镇，地处云南省怒江傈僳族自治州泸水市洛本卓白族乡，紧邻着怒江。这里是怒江州首个易地扶贫搬迁集中安置点，2017年国庆节，金满村首批40户村民入住，2018年最后11户村民入住新居。如今已有搬迁户168户744人，都属于白族支系勒墨人。</p>
					<p>　　村民叁益光的家里干净亮堂，客厅的墙上，挂着一家三口在老房子前的合影。由于山地太陡，找不到平地打地基，老房子都是篱笆为墙、木板为顶、木头为柱的“千脚落地房”的样子。四面透风的房子里面黑黢黢的，下面养牲畜，中间住人，上面放粮食。“一入雨季，屋里就怕漏雨，潮乎乎有虱子”。2017年搬迁前，金满村九成村民就住在这种房子里。</p>
					<p>　　从巴尼小镇往背后的高黎贡山深处走，沿着一条水泥路走上8公里，就回到了金满村村委会。金满村11个村民小组，其中5个不通公路、1个是地质灾害隐患点，这6个组如今已整体搬迁。“最远的马社王底小组有16户人家，到村委会要过悬崖、涉小河、爬陡坡，走上三四个小时。”说起过往，村委会主任沈光干嘘唏不已。</p>
				`
			};
		}
	}
</script>

<style lang="scss">
	.imgbox{
		width: 750rpx;
		height: 440rpx;
		image{
			width: 750rpx;
			height: 440rpx;
		}
	}
	.titlebox{
		width: 680rpx;
		height: 135rpx;
		margin: auto;
		border-bottom: 1px solid #e5e5e5;
	}
	.title{
		width: 405rpx;
		height: 82rpx;
		font-size: 36rpx;
		font-family: PingFang SC;
		font-weight: bold;
		color: #060606;
		line-height: 48rpx;
		margin-top: 35rpx;
	}
	.btnbox{
		text-align: center;
		width: 150rpx;
		image{
			width: 30rpx;
			height: 30rpx;
			margin-top: 35rpx;
		}
		p{
			font-size: 20rpx;
			font-weight: 500;
			color: #656363;
		}
	}
	.richtextbox{
		padding-top: 60rpx;
		padding-left: 35rpx;
		padding-right: 35rpx;
		height: auto;
		margin-bottom: 30rpx;
	}
</style>
