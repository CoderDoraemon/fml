<template>
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
			
		</view>
		
	</view>
</template>

<script>
	
	import uniFav from '../../components/uni-fav/uni-fav.vue'
	export default {
		components: {
			uniFav
		},
		props: {
			
		},
		data() {
			return {
				isattention: false,
				contentText: {
					contentDefault: '关注',
					contentFav: '已关注'
				},
			}
		},
		methods: {
			favClick() {
				this.isattention = !this.isattention
				this.$forceUpdate()
			}
		}
	}
</script>

<style scoped>
	
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
</style>
