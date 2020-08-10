<template>
	<view class="user-space-userinfo">
		<view class="user-space-userinfo-item">
			<view>账号信息</view>
			<view>糗龄：1年3月</view>
			<view>糗百ID：1213</view>
		</view>
		<view class="user-space-userinfo-item">
			<view>个人信息</view>
			<view>职业：IT</view>
			<view>故乡：广东广州</view>
			<view>情感状态：未婚</view>
		</view>
	</view>
</template>

<script>
</script>

<style scoped>
	.user-space-userinfo {
		background-color: #FFFFFF;
		padding: 0 20upx;
	}
	
	.user-space-userinfo-item {
		color: #AAAAAA;
		border-bottom: 1upx solid #E5E5E5;
	}
	
	.user-space-userinfo-item>view {
		padding: 0 0 10upx 0;
	}
	
	.user-space-userinfo-item>view:first-child {
		padding: 20upx 0;
		color: #333333;
	}
</style>
