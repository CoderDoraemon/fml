<template>
	<view class="">
		
		<view class="paper-list u-f-ac">
			<image class="u-f-sh" src="../../static/tabbar/home.png" mode="widthFix"></image>
			<view class="u-f-column u-f1">
				<view class="u-f-ac u-f-jsb">
					<view class="u-line-one">
						昵称昵称昵称昵称昵称昵称昵昵称昵称昵昵称昵称昵昵称昵称昵
					</view>
					
					<view class="">13：58</view>
				</view>
				<view class="u-f-ac u-f-jsb">
					详情
					<uni-badge :text="1" type="error">1</uni-badge>
				</view>
			</view>
		</view>
		
	</view>
</template>

<script>
	import uniBadge from "../../components/uni-badge/uni-badge.vue";
	export default {
		components: {
			uniBadge
		},
		data() {
			return {
				
			}
		},
		methods: {
			
		}
	}
</script>

<style>
	
	.paper-list {
		border-bottom: 1upx solid #e5e5e5;
		padding: 30upx 30upx;
		background: #3F536E;
	}
	.paper-list>image {
		width: 100upx;
		height: 100upx;
		margin-right: 30upx;
	}
	
	.paper-list>view {
	}
	
	.paper-list>view>view>view:last-child {
		background: #007AFF;
		width: 120upx;
		text-align: right;
	}

</style>
