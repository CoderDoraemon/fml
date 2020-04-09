<template>
	<view class="load-more">
		{{ loadtext }}
	</view>
</template>

<script>
	export default {
		props: {
			loadtext: String
		}
	}
</script>

<style>
	.load-more {
		color: #007AFF;
		height: 40upx;
		line-height: 40upx;
		text-align: center;
	}
</style>
