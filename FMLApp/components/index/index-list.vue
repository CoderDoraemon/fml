<template>
	<view class="index-list u-f-column animated fadeIn fast">
		<!-- 头部 -->
		<view class="index-item0 u-f u-f-jsb u-f-ac">
			<!-- 头像 -->
			<view class="avatar-name u-f">
				<!-- 头像 vip -->
				<view class="avatar-vip" @tap="toUserSpace(index)">
					<image class="avatar" :src="item.userpic" mode="widthFix" lazy-load></image>
					<image class="vip" src="../../static/demo/userpic/2.jpg" mode="widthFix"></image>
				</view>
				<!-- 昵称 抬头 -->
				<view class="name-job u-f-column u-f-jsb" >
					<view class="name-tip u-f u-f-ac">
						<text>{{ item.username }}</text>
						<image src="../../static/demo/userpic/3.jpg" mode="widthFix"></image>
					</view>
					<text>优秀UP主</text>
				</view>
			</view>
			<view class="attention-del">
				<text class="attention">+ 关注</text>
				<text class="del">x</text>
			</view>
		</view>
		<!-- 文本内容 -->
		<view class="index-item1">
			{{ item.title }}
		</view>
		<!-- 图片内容 -->
		<view class="index-item2">
			<image :src="item.titlepic" mode="widthFix"></image>
			<view class="icon iconfont icon-bofang index-list-playIcon"></view>
			<view class="index-list-playInfo">
				观看次数
			</view>
		</view>
		<!-- 底部赞踩评论分享 -->
		<view class="index-item3 u-f-ac u-f-jsb">
			<view class="u-f-ac" >
				<view class="u-f-ac icon-margin">
					<view class="iconfont icon-icon_xiaolian-mian"></view>
					1124
				</view>
				<view class="u-f-ac icon-margin">
					<view class="icon iconfont icon-kulian"></view>
					1124
				</view>
			</view>
			<view class="comment u-f-ac">
				<view class="u-f-ac icon-margin">
					<view class="iconfont icon-pinglun1"></view>
					1124
				</view>
				<view class="share u-f-ac">
					<view class="icon iconfont icon-zhuanfa icon-margin"></view>
					1124
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
		methods: {
			toUserSpace(index) {
				this.$emit("toUserSpace", index);
			}
		}
	}
</script>

<style scoped>
	
	.index-list {
		padding: 20upx;
	}
	
	.index-item0 .avatar-name {
		height: 85upx;
	}
	
	.index-item0 .avatar-name .avatar-vip {
		position: relative;
		height: 100%;
	}
	
	.index-item0 .avatar-name .avatar-vip .avatar  {
		width: 85upx;
		height: 85upx;
		border-radius: 85upx;
	}
	
	.index-item0 .avatar-name .avatar-vip .vip {
		width: 25upx;
		height: 25upx;
		border-radius: 25upx;
		position: absolute;
		bottom: 0upx;
		right: 0upx;
	}
	
	.index-item0 .avatar-name .name-job {
		margin-left: 25upx;
		height: 100%;
	}
	
	.index-item0 .avatar-name .name-job .name-tip {
		height: 30upx;
	}
	
	.index-item0 .avatar-name .name-job .name-tip text {
		/* height: 30upx;
		line-height: 30upx; */
		color: #989898;
		font-size: 32upx;
	}
	
	.index-item0 .avatar-name .name-job .name-tip image {
		width: 25upx;
		height: 25upx;
		margin-left: 8upx;
	}
	
	.index-item0 .avatar-name .name-job text {
		line-height: 25upx;
		color: #D5D5D5;
		font-size: 24upx;
	}
	
	.index-item0 .attention-del .attention {
		padding: 5upx 15upx;
		font-size: 30upx;
		background-color: #F4F4F4;
		border-radius: 5upx;
	}
	
	.index-item0 .attention-del .del {
		padding-left: 30upx;
	}
	
	.index-item1 {
		color: #4A4A4A;
		padding: 15upx 0;
	}
	
	.index-item2 {
		position: relative;
	}
	
	.index-item2 .index-list-playIcon {
	}
	
	.index-item2 .index-list-playInfo {
		position: absolute;
		bottom: 8upx;
		right: 8upx;
	}
	
	.index-item2 image {
		width: 100%;
	}
	
	.index-item3 .like {
		color: #C9C9C9;
	}
	
	.index-item3 .comment {
		color: #C9C9C9;
	}
	
	.index-item3 .like .ding {
		padding-right: 15upx;
	}
	
	.index-item3 .comment .message {
		padding-right: 15upx;
	}
	
	.icon-margin {
		margin-right: 10upx;
	}
	
</style>
