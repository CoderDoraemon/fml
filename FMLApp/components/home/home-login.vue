<template>
	<view class="home-login u-f-ac" @tap="tap">
		<view class="u-f1 u-f u-f-ac">
			
			<image class="home-user-avatar " :src="userInfo.avatar" mode="widthFix"></image>
			
			<view class="u-f-column home-user-info">
				<view class="">{{ userInfo.name }}</view>
				<view class="">总帖子 {{ userInfo.total_number }} 今日发帖 {{ userInfo.today_number }}</view>
			</view>
		</view>
		
		<view class="icon iconfont icon-jinru"></view>
	</view>
</template>

<script>
	export default {
		props: {
			userInfo: Object,
		},
		methods: {
			tap() {
				uni.navigateTo({
					url: '../../pages/home-page/home-page'
				})
			}
		}
	}
</script>

<style scoped>
	.home-login {
		padding: 20upx;
		height: 100upx;
	}
	
	.home-user-avatar {
		width: 100upx;
		height: 100upx;
		margin-right: 16upx;
		border-radius: 100upx;
	}
	
	.home-user-info {
	}
</style>
