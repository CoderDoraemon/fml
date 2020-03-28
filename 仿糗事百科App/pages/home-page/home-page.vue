<template>
	<view>
		<!-- 头部面板 -->
		<view class="user-info u-f-ac">
			<view class="user-info-avatar">
				<image src="../../static/demo/userpic/1.jpg" mode="widthFix"></image>
			</view>
			
			<view class="u-f-column u-f1">
				<home-tabs :numbers="numbers"></home-tabs>
				<button type="primary">关注</button>
			</view>
		</view>
		
		<swiper-tab-head
		:tabBars="tabBars" 
		:tabIndex="tabIndex" 
		@tabtap="tabtap"
		:itemWidth="itemWidth">
		</swiper-tab-head>
	</view>
</template>

<script>
	import homeTabs from '../../components/home/home-tabs.vue';
	import swiperTabHead from '../../components/index/swiper-tab-head.vue'
	export default {
		components: {
			homeTabs,
			swiperTabHead
		},
		data() {
			return {
				tabIndex: 0,
				numbers: [
					{
						title: "获赞",
						number: 37
					},
					{
						title: "动态",
						number: 46
					},
					{
						title: "评论",
						number: 12
					}
				],
				tabBars: [{
						name: "主页",
						id: "guanzhu"
					},
					{
						name: "帖子",
						id: "tuijian"
					},
					{
						name: "动态",
						id: "tiyu"
					}
				],
			}
		},
		methods: {
			/* tab item 点击 */
			tabtap(index) {
				console.log("点击" + index)
				this.tabIndex = index;
			},
		}
	}
</script>

<style>
	
	.user-info {
		padding: 40upx 20upx;
		border-bottom: 1px solid #E5E5E5;
	}
		
	.user-info .user-info-avatar image {
		width: 150upx;
		height: 150upx;
		border-radius: 100%;
		margin-right: 30upx;
	}
	
</style>
