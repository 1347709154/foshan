<template>
	<view class="content">
		<u-parse :html="richtext"></u-parse>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				richtext:`<p style="text-align:justify;text-indent:2em;">尊敬的游客，欢迎光临三峡文物园景区，为确保景区正常的参观秩序和游客及文物的安全，请仔细阅读以下提示：</p>
					<p style="text-align:justify;text-indent:2em;">*景区现实行免费开放，无需购票。景区核定最大游客承载3000人，如达到此接待量，将暂停游客进入景区。</p>
					<p style="text-align:justify;text-indent:2em;">*未成年人须有监护人带领参观；高龄老人、行动不便者须有亲属陪伴参观。</p>
					<p style="text-align:justify;text-indent:2em;">*禁止携带管制刀具，易燃易爆、烟火爆竹等危险品进入景区。</p>
					<p style="text-align:justify;text-indent:2em;">*衣冠不整者、携带宠物者、酗酒者请勿入园。</p>
					<p style="text-align:justify;text-indent:2em;">*参观过程中，请注意景区的安全警示标志，遵守游览秩序，请勿吸烟、乱刻乱画、攀爬、翻越、打闹、上下台阶请小心谨慎。</p>
					<p style="text-align:justify;text-indent:2em;">*请保管好自己的随身物品，以防遗失。</p>
					<p style="text-align:justify;text-indent:2em;">*请勿随地大小便、吐痰、乱扔果皮、纸屑等废弃物，保持景区清洁卫生。</p>
					<p style="text-align:justify;text-indent:2em;">*请爱护文物、展品、花木及其他公共设施，如有损坏，须照价赔偿。</p>
					<p style="text-align:justify;text-indent:2em;">*如需帮助，请拨打景区电话：023-55182111</p>
				`
			};
		}
	}
</script>

<style lang="scss">
	.content{
		padding: 0 34rpx;
	}
</style>
