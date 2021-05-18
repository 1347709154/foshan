<template>
	<view class="content" >
		<view class="from">
		   <u-field  label="发票抬头" placeholder="请输入公司名称（必填）"></u-field>	
		   <u-field  label="识别号" placeholder="(选填）"></u-field>	
		   <u-field  label="电子邮箱" placeholder="(必填）"></u-field>
		   <u-field  label="注册地址" placeholder="(选填）"></u-field>
		   <u-field  label="注册电话" placeholder="(选填）"></u-field>
		   <u-field  label="开户银行" placeholder="(选填）"></u-field>
		   <u-field  label="银行账户" placeholder="(选填）" :border-bottom="false"></u-field>
		</view>
		<u-radio-group class="radio">
		    <u-radio shape="circle"  style="color: #333333;" >设为默认发票抬头</u-radio>
		</u-radio-group>
		<view class="Submit">保存</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {

		},
		methods: {

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
		/* align-items: center;
		justify-content: center; */
	}
	.from{
		background: #ffffff;
		margin-top: 30rpx;
		width: 96%;
		border-radius: 20rpx;
		padding: 20rpx;
		margin-left: 2%;
	}
	.radio{
		width: 96%;
		margin-left: 2%;
		text-align: left;
		margin-top: 20rpx;
		
	}
	.Submit{
		width: 90%;
		margin-left: 5%;
		height: 70rpx;
		line-height: 70rpx;
		background: #15A03F;
		color: #ffffff;
		font-size: 32rpx;
		text-align: center;
		border-radius: 35rpx;
		margin-top: 150rpx;
	}
</style>
