<template>
	<view class="topic-list u-f animated fadeIn faster p-2" @tap="opendetail"
	hover-class="bg-light-secondary"> 
		<image :src="item.titlepic" mode="widthFix" lazy-load 
		class="rounded mr-2"></image>
		<view>
			<view>#{{item.title}}#</view>
			<view class="text-light-muted">{{item.desc}}</view>
			<view class="text-light-muted">动态 {{item.totalnum}} 今日 {{item.todaynum}}</view>
		</view>
	</view>
</template>

<script>
	export default {
		props:{
			ischange:{
				type:Boolean,
				default:false
			},
			item:Object,
			index:Number
		},
		methods:{
			opendetail(){
				if (this.ischange) {
					// 通知并返回
					uni.$emit('changeTopic',{ 
						id:this.item.id, 
						title:this.item.title,
					});
					uni.navigateBack({ delta: 1 });
					return;
				}
				uni.navigateTo({
					url: '../../pages/topic-detail/topic-detail?detail='+JSON.stringify(this.item),
				});
			}
		}
	}
</script>

<style scoped>
.topic-list image{
	width: 150upx;
	height: 150upx;
}
.topic-list>view>view:first-child{
	font-size: 32upx;
}
</style>
