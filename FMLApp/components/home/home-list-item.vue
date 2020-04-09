<template>
	<view class="home-list-item u-f" hover-class="home-list-item-hover">
		<view class="home-list-item-left u-f-ac u-f1">
			<template v-if="item.icon">
				<view class="home-list-item-left-icon icon iconfont" :class="['icon-'+item.icon]"></view>
			</template>
			<view class="">{{ item.title }}</view>
		</view>
		<view class="u-f-ac icon iconfont icon-jinru"></view>
	</view>
</template>

<script>
	
	export default {
		props: {
			item: Object,
			index: Number
		}
	}
	
</script>

<style scoped>
	
	
	
	.home-list-item {
		height: 100upx;
		padding: 0 30upx;
	}
	/* 箭头 */
	.home-list-item>view:last-child {
		/* padding-right: 30upx; */
	}
	
	.home-list-item-hover {
		background: #E5E5E5;
	}
	
	.home-list-item-left {
		font-size: 30upx;
	}
	
	.home-list-item-left-icon {
		margin-right: 16upx;
		font-size: 45upx;
	}
</style>
