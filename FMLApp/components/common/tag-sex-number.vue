<template>
	<view class="user-sex icon iconfont icon-nan" :class="[isman == 1 ? 'icon-nan': 'icon-nv']">{{ age }}</view>
</template>

<script>
	export default {
		props: {
			age: String,
			isman: String
		},
		data() {
			return {
				
			}
		}
	}
</script>

<style>
	.user-sex {
		background-color: #4C99FF;
		color: #FFFFFF;
		font-size: 22upx;
		padding: 5upx 15upx;
		line-height: 24upx;
		border-radius: 24upx;
		margin-left: 8upx;
	}
</style>
