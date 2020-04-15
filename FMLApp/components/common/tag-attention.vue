<template>
	<view class="icon iconfont icon-zengjia" :class="[isMan ? 'icon-nan': 'icon-nv']">{{ age }}</view>
</template>

<script>
	export default {
		props: {
			age: {
				type: Number,
				default: 0
			},
			isMan: {
				type: Boolean,
				default: true
			}
		},
		data() {
			
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
