<template>
	<view class="content">
		<view class="item-list" v-for="item in listdata" @tap="goinfo(item.title)">
			<view class="title">
				{{item.title}}
			</view>
			<view class="bottom">
				<view class="left time">
					{{item.time}}
				</view>
				<view class="right addr">
					{{item.addres}}
				</view>
			</view>
		</view>
		<u-loadmore :status="status" :icon-type="iconType" :load-text="loadText" />
	</view>
</template>

<script>
	export default {
		data() {
			return {
				listdata:[
					{
					title:'文化和旅游部公告',
					addres:'佛顶山生态旅游景区',
					time:'20521-02-07 15:11:12'
					},
					{
					title:'贵州省政府公告',
					addres:'佛顶山生态旅游景区',
					time:'20521-02-07 15:11:12'
					},
					{
					title:'贵阳市政府公告',
					addres:'佛顶山生态旅游景区',
					time:'20521-02-07 15:11:12'
					},
					{
					title:'文化和旅游部公告',
					addres:'佛顶山生态旅游景区',
					time:'20521-02-07 15:11:12'
					},
					{
					title:'文化和旅游部公告',
					addres:'佛顶山生态旅游景区',
					time:'20521-02-07 15:11:12'
					},
					{
					title:'文化和旅游部公告',
					addres:'佛顶山生态旅游景区',
					time:'20521-02-07 15:11:12'
					},
					{
					title:'文化和旅游部公告',
					addres:'佛顶山生态旅游景区',
					time:'20521-02-07 15:11:12'
					},
				],
				list: 1,
				page: 0,
				status: 'loadmore',
				iconType: 'flower',
				loadText: {
					loadmore: '轻轻上拉',
					loading: '努力加载中',
					nomore: '实在没有了'
				}
			}
		},
		methods: {
			goinfo(text){
				uni.navigateTo({
					url:"./noticeinfo?title="+text
				})
			}
		},
		onReachBottom() {
			if (this.page >= 3) return;
			this.status = 'loading';
			this.page = this.page+1;
			setTimeout(() => {
				// this.list += 1;
				if (this.page >= 3) this.status = 'nomore';
				else this.status = 'loading';
			}, 2000)
		}
	}
</script>

<style lang="scss">
	page {
		background-color: #F5F3F3;
	}

	.item-list {
		width: 100%;
		padding: 0px 38rpx;
		height: 188rpx;
		margin-top: 9rpx;
		background: #FFFFFF;
	}
	.title{
		font-size: 18px;
		font-weight: 600;
		margin-top: 38rpx;
	}
	.bottom{
		margin-top: 60rpx;
		font-size: 12px;
		color: #686666;
	}
</style>
