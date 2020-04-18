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
			
			<common-list-playcover :showType="item.showtype" :imageURL="item.titlepic"></common-list-playcover>
			
			<view class="u-f u-f-jsb">
				<view class="">{{ item.path }}</view>
				<view class="u-f-ajc" >
					<view class="u-f-ajc icon iconfont icon-zhuanfa">{{ item.sharenum }}</view>
					<view class=" icon iconfont icon-pinglun1">{{ item.commentnum }}</view>
					<view class=" icon iconfont icon-dianzan1">{{ item.goodnum }}</view>
				</view>
			</view>
		</view>
	
	</view>
</template>

<script>
	
	import commonListPlaycover from './common-list-playcover.vue'
	import commonIconfont from './common-iconfont.vue'
	
	export default {
		components: {
			commonListPlaycover,
			commonIconfont
		},
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
	
	.common-list-r>view:nth-child(3) {
		margin-bottom: 15upx;
	}
	
	.common-list-r>view:nth-child(4) {
		color: #C1C1C1;
		font-size: 28upx;
		width: 100%;
		border: 1upx solid #09BB07;
	}
	.common-list-r>view:nth-child(4)>view:nth-child(2) {
		border: 1upx solid #09BB07;
	}
	
	.common-list-r>view:nth-child(4)>view:nth-child(2)>view {
		margin-left: 15upx;
		padding-left: 8upx;
		border: 1upx solid #0081FF;
	}
</style>
