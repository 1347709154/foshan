<template>
	<view class="content">
		<view class="top"></view>
		<!-- 身份证信息 -->
		<view class="card-inpt">
			<view class="user-name">
				<view style="line-height: 100rpx;">
					<text style="color: red;">*</text>
					<label>真实姓名</label>
				</view>
				<view class="user-name-ipt" style="margin-left: 10rpx;">
					<input placeholder-style="font-size: 22rpx;" placeholder="请输入您的真实姓名，认证后不可更改"/>
					</view>
			</view>
			<view class="user-name">
				<view style="line-height: 100rpx;">
					<text style="color: red;">*</text>
					<label>身份证号</label>
				</view>
				<view class="user-name-ipt" style="margin-left: 10rpx;">
					<input type="idcard" placeholder-style="font-size: 22rpx;" placeholder="请输入您的真实姓名对应的身份证号"/>
					</view>
			</view>
		</view>
		<!-- 上传照片 -->
		<view class="img-card">
			<view class="img-card-tetel">请上传身份证照片</view>
			<view class="idcard-img">
				<view class="idcard-img-box" style="margin-right: 20rpx;">
					<image src="/static/user/idcard-1.png" mode="aspectFill"></image>
				</view>
				<view class="idcard-img-box">
					<image src="/static/user/idcard-2.png" mode="aspectFill"></image>
				</view>
			</view>
			<view class="idcard-tel">
				<image src="/static/user/sigh.png" mode="scaleToFill"></image>
				<view class="idcard-tel-te">
					<view>证件必须是清晰彩色原件电子版本。可以是扫描件或者数码拍摄 照片。</view>
					<view>支持jpg、png、jpeg的图片格式</view>
				</view>
			</view>
			<view class="Submit">确定上传</view>
		</view>
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
		background: #EDEDED;
	}
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	.top{
		background: #15A03F;
		height: 300rpx;
		width: 100%;
	}
	/* 身份信息 */
	.card-inpt{
		background: #ffffff;
		width: 96%;
		height: 300rpx;
		border-radius: 10rpx;
		margin-top: -200rpx;
		padding: 0rpx 32rpx;
	}
	.user-name{
	/* 	height: 150rpx; */
		width: 100%;
		display: flex;
		flex-direction: row;
		font-size: 30rpx;
		font-weight: bold;
		margin-top: 30rpx;
	}
	.user-name-ipt{
		border: 1rpx solid #ddd;
		height: 80rpx;
		margin-top: 15rpx;
		padding: 0rpx 10rpx;
		width: 480rpx;
	}
	.user-name-ipt>input{
		height: 80rpx;
		line-height: 80rpx;
		font-size: 28rpx;
		color: #000000;
	
	}
	/* 上传照片 */
	.img-card{
		background: #ffffff;
		border-radius: 15rpx;
		height: 800rpx;
		width: 96%;
		margin-top: 30rpx;
		padding: 0 20rpx;
	}
	.img-card-tetel{
		margin-top: 50rpx;
		color: #999999;
		font-size: 32rpx;
		font-weight: bold;
		text-align: left;
	}
	.idcard-img{
		margin-top: 50rpx;
		height: 300rpx;
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
	}
	.idcard-img-box{
		background: #F0F8FA;
		padding: 10rpx;
		border: 2rpx dashed  #DCE4E5;
		
	}
	.idcard-img-box>image{
		width: 310rpx;
		height: 250rpx;
	}
	.idcard-tel{
		margin-top: 30rpx;
		text-align: left;
		display: flex;
		flex-direction: row;
	}
	.idcard-tel>image{
		width: 48rpx;
		height: 40rpx;
		margin-top: 25rpx;
	}
	.idcard-tel-te{
		display: flex;
		flex-direction: column;
		margin-left: 10rpx;
		font-size: 24rpx;
		color: #999999;
	}
	.Submit{
		width: 250rpx;
		height: 80rpx;
		line-height: 80rpx;
		font-size: 32rpx;
		font-weight: bold;
		text-align: center;
		color: #FFFFFF;
		background: #3B4D71;
		margin-left: 35%;
		margin-top: 100rpx;
	}
</style>
