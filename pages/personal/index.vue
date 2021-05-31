<template>
	<view class="content">
		<view class="user-img">
			<image src="../../static/user/user_img-1.png" mode="scaleToFill"></image>
		</view>
		<view class="card">
			<u-field  type="text"  v-model="user_name" label="昵称" 
			placeholder="请输入您的昵称"></u-field>
			<u-field v-model="mobile" type="number" label="手机" placeholder="请填写手机号">
				<u-button size="mini" slot="right"  @click="getCode">更换手机号</u-button>
			</u-field>
			<u-cell-item  title="性别"  :arrow="false" class="radio" >
				<view style="float: left;margin-left: 70rpx;">
					<label class="radio"><radio value="1" :checked="sex==='1'" @click="radio('1')" color="#333" style="transform:scale(0.7)"/>男</label>
					<label class="radio"><radio value="2" :checked="sex==='2'" @click="radio('2')" color="#333" style="transform:scale(0.7)"/>女</label>
				</view>
			</u-cell-item>
			<u-field  type="text"  v-model="user_name" label="签名"
			placeholder="请输入您的签名"></u-field>
		</view>
		<view class="bottom">保存</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello',
				user_name:'',
				mobile:'',
				sex:'1',
				
			}
		},
		onLoad() {

		},
		methods: {
			getCode:function(e){
				console.log(111111111)
			},
			radio:function(e){
				this.sex=e;
			}
		}
	}
</script>

<style>
	page{
		background: #F2F6F7;
	}
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	.user-img{
		height: 400rpx;
		width: 100%;
		background: #ffffff;
		display: flex;
		flex-direction: row;
	/* 	align-items: center; */
		justify-content: center;
	}
	.user-img>image{
		width: 170rpx;
		height: 170rpx;
		border-radius: 50%;
		margin-top: 180rpx;
	}
	.card{
		width: 100%;
		background: #ffffff;
		margin-top: 30rpx;
		padding: 0 32rpx;
	}
	.user-mobile{
		height: 80rpx;
		border-bottom: 1rpx solid #ddd;
	}
	.cell-item{
		color: #000000;
	}
	.radio{
		text-align: left;
		
	}
	.bottom{
		margin-top: 50rpx;
		width: 90%;
		height: 80rpx;
		line-height: 80rpx;
		text-align: center;
		background:#FF9726 ;
		color: #FFFFFF;
	}
</style>
