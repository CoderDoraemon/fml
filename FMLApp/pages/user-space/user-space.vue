<template>
	<view>
		<!-- 头部面板 -->
		<view class="user-space-top u-f-ajc u-f-column u-p-r">
			
			<image src="../../static/bgimg/1.jpg" mode="aspectFill" lazy-load></image>
			
			<view class="user-space-info u-p-a u-f-column u-f-ajc">
				<view>
					<image src="../../static/demo/userpic/1.jpg" mode="widthFix" lazy-load></image>
				</view>
				
				<view class="user-space-info-name u-f u-f-ajc">
					昵称
					<tag-sex-number age="20" isman="1"></tag-sex-number>
				</view>
				
				<view class="user-space-info-att">
					<uni-fav 
					:content-text="contentText" 
					iconText="plusempty" 
					:checked="isattention" 
					class="favBtn" 
					:circle="true" 
					bg-color="#FBE95C" 
					bg-color-checked="#007aff" 
					fg-color="#333333" 
					fg-color-checked="#ffffff" 
					@click="favClick" />
				</view>
				
				<!-- <home-tabs class="home-tabs-info" :numbers="numbers"></home-tabs> -->
			</view>
			
		</view>
		
		<view class="home-tabs-info u-p-r">
			<home-tabs :numbers="numbers"></home-tabs>
		</view>
		
		
		<view class="user-space-segmentation"></view>
		
		<!-- <swiper-tab-head
		:tabBars="tabBars" 
		:tabIndex="tabIndex" 
		scrollItemStyle="width:33.33%;" 
		scrollStyle="border-bottom: 4px;"
		@tabtap="tabtap">
		</swiper-tab-head> -->
		
		<swiper-tab-head :tabBars="tabBars" :layoutType="2" :currentIndex="tabIndex" @tabSelect="tabSelect"></swiper-tab-head>
		
	</view>
</template>

<script>
	import homeTabs from '../../components/home/home-tabs.vue';
	import swiperTabHead from '../../components/index/swiper-tab-head.vue'
	import tagSexNumber from '../../components/common/tag-sex-number.vue'
	import uniFav from '../../components/uni-fav/uni-fav.vue'
	
	export default {
		components: {
			homeTabs,
			swiperTabHead,
			tagSexNumber,
			uniFav
		},
		data() {
			return {
				tabIndex: 0,
				
				scrollLeft: 0,
				TabCur: 0,
				itemWidth: 0,
				isattention: false,
				contentText: {
					contentDefault: '关注',
					contentFav: '已关注'
				},
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
		mounted() {
			
		},
		methods: {
			/* tab item 点击 */
			tabSelect(index) {
				this.tabIndex = index;
			},
			favClick() {
				this.isattention = !this.isattention
				this.$forceUpdate()
			}
		}
	}
</script>

<style>
	
	.favBtn {
		margin: 0 20rpx 20rpx 0;
	}
	
	.user-space-top>image {
		width: 100%;
		height: 600upx;
	}
	
	.user-space-info {
		width: 100%;
		bottom: 30upx;
	}
	
	.user-space-info>view:nth-child(1)>image {
		width: 90upx;
		height: 90upx;
		border-radius: 90upx;
	}
	
	.user-space-info-name {
		font-size: 24upx;
		color: #FFFFFF;
		margin: 20upx 0;
	}
	
	.user-space-info-guanzhu {
		background-color: #FAE85C;
		color: #333333;
		font-size: 25upx;
		border-radius: 10upx;
		width: 100upx;
	}
	
	.home-tabs-info {
		border-radius: 20upx 20upx 0 0;
		z-index: 10;
		margin-top: -20upx;
		/* border-top-left-radius: 20upx;
		border-top-right-radius: 20upx; */
	}
	
	.user-space-segmentation {
		background-color: #F4F4F4;
		height: 20upx;
	}
	
</style>
