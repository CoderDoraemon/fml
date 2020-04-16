<template>
	<view class="home-info u-f-ac animated fadeIn fast" @tap="ToUserSpace">
		<f-image :src="homeinfo.userpic"
		errorText="失败"
		imageClass="rounded-circle mr-2" 
		imageStyle="width:100rpx;height:100rpx;font-size:15rpx;"
		@click.stop="openSpace"></f-image>
		<view class="u-f1">
			<view class="font-lg text-dark">{{homeinfo.username}}</view>
			<view class="main-light-dark font">
				<text class="mr-2">总帖子 {{homeinfo.totalnum}}</text>
				<text>今日发帖 {{homeinfo.todaynum}}</text>
			</view>
		</view>
		<view class="icon iconfont icon-jinru"></view>
	</view>
</template>

<script>
	import fImage from '@/components/common/f-image.vue';
	export default {
		components: {
			fImage
		},
		props:{
			homeinfo:Object
		},
		methods:{
			ToUserSpace(){
				this.User.navigate({
					url: '../../pages/user-space/user-space?userid='+this.homeinfo.id,
				});
			}
		}
	}
</script>

<style scoped>
.home-info{
	padding: 20upx 40upx;
}
.home-info>view:first-of-type>view:first-child{
	font-weight: bold;
}
.home-info>view:last-of-type{
	height: 100%;
}

</style>
