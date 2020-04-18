<template>
	<view class="common-list-playcover u-p-r u-f-ajc">
		<image :src="imageURL" mode="widthFix" lazy-load></image>
		<block v-if="showType===1">
			<view class="play-image u-p-a u-f-ajc icon iconfont icon-bofang"></view>
			<view class="play-info u-p-a">
				20w 次播放2：47
			</view>
		</block>
	</view>
</template>

<script>
	
	/* 
	* 属性
	* @property {Number} showType = 【0|1】【图片|视频】
	 */
	export default {
		props: {
			showType: {
				type: Number,
				default: 0
			},
			imageURL: {
				type: String,
				default: ""
			},
			imageRadius: {
				type: Number,
				default: 0
			}
		},
		data() {
			return {
				
			}
		}
	}
</script>

<style>
	
	.common-list-playcover>image {
		border-radius: 10upx;
		width: 100%;
	}
	
	.play-image {
		font-size: 120upx;
		color: #FFFFFF;
		height: 120upx;
		width: 120upx;
		left: 50%;
		top: 50%;
		margin-left: -60upx;
		margin-top: -60upx;
	}
	
	.play-info {
		color: #FFFFFF;
		right: 8upx;
		bottom: 0;
		background-color: rgba(58, 55, 54, 0.6);
		font-size: 24upx;
		border-radius: 24upx;
		padding: 0 10upx;
	}
</style>
