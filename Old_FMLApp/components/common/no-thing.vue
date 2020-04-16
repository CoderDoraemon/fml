<template>
	<view class="nothing u-f-ajc animated fadeIn" :style="getStyle">
		<image src="/static/common/nothing.png"  
		style="width: 350rpx;height: 350rpx;"></image>
		<view class="text-center pt-1 font-md text-light-black">什么都没有</view>
	</view>
</template>

<script>
	export default {
		props: {
			position: {
				type: Boolean,
				default: true
			},
		},
		computed: {
			getStyle() {
				return this.position ? `
					position: absolute;
					top: 0;
					left: 0;
					right: 0;
					bottom: 0;
				` : 'padding:30rpx 0;'; 
			}
		},
	}
</script>

<style>
	.nothing{
		background: #FFFFFF;
		flex-direction: column;
	}
</style>
