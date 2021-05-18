<template>
	<view class="content">
		<view class="box">
			<view class="listxitem" v-for="item in list" @tap="goinfo">
				<view class="topimg">
					<image :src="item.bimg" mode=""></image>
				</view>
				<view class="text">
					{{item.name}}
				</view>
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
						bimg:'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fattach.bbs.miui.com%2Fforum%2F201303%2F16%2F173710lvx470i4348z6i6z.jpg&refer=http%3A%2F%2Fattach.bbs.miui.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1623920602&t=66563a6ea0ebe58cbcb2eccbef7aead0',
						name:'金顶云海'
					},
					{
						bimg:'https://ss1.baidu.com/-4o3dSag_xI4khGko9WTAnF6hhy/zhidao/pic/item/ca1349540923dd54ea2076a4d309b3de9d8248af.jpg',
						name:'飞凤朝阳'
					},
					{
						bimg:'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fattach.bbs.miui.com%2Fforum%2F201311%2F29%2F211325omg8g31kv1rh2nbg.jpg&refer=http%3A%2F%2Fattach.bbs.miui.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1623920614&t=ccfb953d1f43daede2f9bdb0315cd08f',
						name:'金顶云海'
					},
				]
			};
		},
		methods:{
			goinfo(){
				uni.navigateTo({
					url:"../scenic/scenic"
				})
			}
		}
	}
</script>

<style lang="scss">
	.box{
		padding: 0 20rpx;
		display: flex;
		width: 100%;
		// min-height: 800rpx;
		height: auto;
		justify-content: space-between;
		flex-wrap: wrap;
		
	}
	.listxitem{
		margin-top: 20rpx;
		width: 350rpx;
		height: 350rpx;
	}
	.topimg{
		width: 350rpx;
		height: 280rpx;

		image{
			width: 350rpx;
			height: 280rpx;
			border-radius: 18rpx;
		}
	}
	.text{
		margin-top: 20rpx;
	}
</style>
