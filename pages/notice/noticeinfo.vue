<template>
	<view class="content">
		<view class="title">
			{{title}}
		</view>
		<view class="text">
			{{text}}
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title:'',
				text:'为加强旅游景区质量管理，提升旅游景区品质，净化旅游消费环境，依照中华人民共和国国家标准《旅游景区质量等级的划分与评定》（GB/T 17775-2003）与《旅游景区质量等级管理办法》，根据5A级旅游景区年度复核结果，文化和旅游部决定，对复核检查严重不达标或存在严重问题的7家5A级旅游景区处理如下： 　 （一）给予山西省晋中市乔家大院景区取消旅游景区质量等级处理； （二）给予辽宁省沈阳市沈阳植物园景区、浙江省温州市雁荡山景区、河南省焦作市云台山景区、广东省梅州市雁南飞茶田景区、四川省乐山市峨眉山景区、云南省昆明市石林景区等6家景区通报批评责令整改处理，限期3个月。 现予公告。 　　 文化和旅游部 2019年7月31日'
			}
		},
		onLoad(option) {
			this.title=option.title
			uni.setNavigationBarTitle({
				title:option.title
			})
		},
		methods: {
			
		}
	}
</script>

<style lang="scss">
	.title{
		font-size: 22px;
		margin-top: 76rpx;
	}
	.text{
		padding: 0 35rpx;
		margin-top: 56rpx;
	}
	
</style>
