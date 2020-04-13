<template>
	<view class="common-list u-f">
		<!-- 左边信息 -->
		<view class="common-list-l">
			<image :src="item.userpic" mode="widthFix" lazy-load></image>
		</view>
	
		<!-- 右边信息 -->
		<view class="common-list-r u-f1">
			<view class="u-f-ac u-f-jsb">
				<view class="u-f-ac">
					<view class="">{{ item.username }}</view>
					<view class="user-sex icon iconfont icon-nan">{{ item.age }}</view>
				</view>
				<view class="u-f-ac">
					<view class="user-attention icon iconfont icon-zengjia">关注</view>
					<view class="icon iconfont icon-guanbi"></view>
				</view>
			</view>
			<view>{{ item.title }}</view>
			<view class="u-p-r u-f-ajc">
				<image :src="item.titlepic" mode="widthFix" lazy-load></image>
				<view class="common-list-play u-p-a u-f-ajc icon iconfont icon-bofang"></view>
				<view class="common-list-playInfo u-p-a">
					20w 次播放2：47
				</view>
			</view>
			<view class="u-f u-f-jsb">
				<view class="">{{ item.path }}</view>
				<view class="u-f-ac">
					<view class="icon iconfont icon-zhuanfa">{{ item.sharenum }}</view>
					<view class="icon iconfont icon-pinglun1">{{ item.commentnum }}</view>
					<view class="icon iconfont icon-dianzan1">{{ item.goodnum }}</view>
				</view>
			</view>
		</view>
	
	</view>
</template>

<script>
	
	export default {
		props: {
			item: Object,
			index: Number
		},
		data() {
			return {
				
			}
		}
	}
	
</script>

<style scoped>
	.common-list {
		padding: 20upx;
		border-bottom: 1upx solid #E5E5E5;
	}
	
	.common-list-l {
		flex-shrink: 0;
	}
	
	.common-list-l image {
		width: 90upx;
		height: 90upx;
		border-radius: 100%;
	}
	
	.common-list-r {
		margin-left: 12upx;
	}
	
	.common-list-r>view:nth-child(1)>view:first-child .user-sex {
		background-color: #4C99FF;
		color: #FFFFFF;
		font-size: 22upx;
		padding: 5upx 15upx;
		line-height: 24upx;
		border-radius: 24upx;
		margin-left: 8upx;
	}
	
	.common-list-r>view:nth-child(1)>view:last-child .user-attention {
		background-color: #F3F3F3;
		color: #333333;
		font-size: 22upx;
		padding: 5upx 15upx;
		line-height: 24upx;
		border-radius: 5upx;
		margin-right: 8upx;
	}
	
	.common-list-r>view:nth-child(2) {
		font-size: 32upx;
		padding: 12upx 0;
	}
	
	.common-list-r>view:nth-child(3) image {
		width: 100%;
		border-radius: 10upx;
	}
	
	.common-list-r>view:nth-child(3) {
		margin-bottom: 15upx;
	}
	
	.common-list-play {
		font-size: 120upx;
		color: #FFFFFF;
		height: 120upx;
		width: 120upx;
		left: 50%;
		top: 50%;
		margin-left: -60upx;
		margin-top: -60upx;
	}
	
	.common-list-playInfo {
		color: #FFFFFF;
		right: 8upx;
		bottom: 0;
		background-color: rgba(58, 55, 54, 0.6);
		font-size: 24upx;
		border-radius: 24upx;
		padding: 0 10upx;
	}
	
	.common-list-r>view:nth-child(4) {
		color: #C1C1C1;
		font-size: 28upx;
	}
	
	.common-list-r>view:nth-child(4)>view:nth-child(2)>view {
		margin-left: 15upx;
		padding-left: 8upx;
	}
</style>
