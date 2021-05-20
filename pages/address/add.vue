<template>
	<view class="content">
		<view class="add-card">
			<u-field  label="联系人" placeholder="请填写联系人"></u-field>
			<u-cell-item  title="性别"  :arrow="false" class="radio"  >
				<view style="float: left;margin-left: 70rpx;">
					<label class="radio"><radio value="1" :checked="sex==='1'" @click="radio('1')" color="#04753D" style="transform:scale(0.7)"/>男</label>
					<label class="radio" style="margin-left: 100rpx;"><radio value="2" :checked="sex==='2'" @click="radio('2')" color="#04753D" style="transform:scale(0.7)"/>女</label>
				</view>
			</u-cell-item>
			<u-field  label="手机号" placeholder="请填写手机号"></u-field>
			<u-field  label="地址" placeholder="请选择" :disabled="true" right-icon="arrow-right" @tap="getLocation"></u-field>
			<u-field  label="门牌号" placeholder="如：5号楼108室"></u-field>
			<u-cell-item  title="标签"  :arrow="false" class="tag"  >
				<view class="van-tag">
					<view  @tap="tags(1)" :class="[tag=='1'?'tag-lists':'tag-list']">公司</view>
					<view  @tap="tags(2)" :class="[tag=='2'?'tag-lists':'tag-list']">家</view>
					<view  @tap="tags(3)" :class="[tag=='3'?'tag-lists':'tag-list']">学校</view>
				</view>	
			</u-cell-item>
			<u-cell-item  title="默认地址"  :arrow="false" class="tag"> 
				<switch checked="checked" @change="switch1Change" color="#009944" />
			</u-cell-item>
		</view>
		<view class="bt">保存</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello',
				sex:'1',
				tag:'1',
				checked: true,
			}
		},
		onLoad() {

		},
		methods: {
			//性别选择
			radio:function(e){
				this.sex=e;
			},
			//标签选择
			tags:function(e){
				console.log(e)
				this.tag=e
			},
			//默认地址开关
			switch1Change: function (e) {
				this.checked=e.target.value
			},
			//打开地图选择位置
			getLocation:function(e){
				
			}
			
		}
	}
</script>

<style>
	page{
		background: #F5F5F5;
	}
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	.add-card{
		width: 94%;
		border-radius: 20rpx;
		background: #ffffff;
		margin-top: 30rpx;
	}
	.radio{
		color: #000000;
	}
	.tag{
		color: #000000;
	}
	.van-tag{
		display: flex;
		flex-direction: row;
		text-align: left;
		margin-left: 40rpx;
	}
	.tag-list{
		margin-left: 40rpx;
		border-radius: 20rpx;
		background: #F5F5F5;
		color: #A0A0A0;
		width: 80rpx;
		border-radius: 10rpx;
		margin-left: 50rpx;
		text-align: center;
	}
	.tag-lists{
		background: #15A03F;
		border-radius: 10rpx;
		color: #ffffff;
		margin-left: 50rpx;
		width: 80rpx;
		text-align: center;
	}
	.bt{
		position: absolute;
		bottom: 60rpx;
		background: #07C160;
		color: #ffffff;
		text-align: center;
		height: 80rpx;
		line-height: 80rpx;
		width: 80%;
		border-radius: 40rpx;
	}
</style>
