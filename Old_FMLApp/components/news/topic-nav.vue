<template>
	<view class="topic-nav py-2 px-2">
		<view class="u-f-ac u-f-jsb">
			<view>热门分类</view>
			<view class="u-f-ac text-light-muted animated faster" 
			@tap="openTopicNav" hover-class="pulse main-color">
				更多<view class="icon iconfont icon-jinru"></view>
			</view>
		</view>
		<view class="u-f-ac mb-1 mt-2">
			<block v-for="(item,index) in nav" :key="index">
				<view hover-class="pulse main-bg-color text-white border-white"
				class="u-f-ajc bg-light-secondary main-light-dark rounded animated faster border border-light-secondary">{{item.name}}</view>
			</block>
		</view>
	</view>
</template>

<script>
	export default {
		props:{
			nav:Array
		},
		methods:{
			openTopicNav(){
				uni.navigateTo({
					url: '../../pages/topic-nav/topic-nav',
				});
			}
		}
	}
</script>

<style scoped>
.topic-nav>view:first-child{
	margin-bottom: 10upx;
}
.topic-nav>view:first-child>view:first-child{
	color: #333333;
	font-size: 32upx;
}
.topic-nav>view:last-child>view{
	flex: 1;
	margin: 0 10upx;
}
</style>
