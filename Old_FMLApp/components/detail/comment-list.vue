<template>
	<view class="uni-comment-list" :class="{'u-comment-list-child':(item.fid>0)}">
		<view class="uni-comment-face">
			<f-image :src="item.userpic"
			errorText="失败"
			imageClass="rounded-circle mr-2 border" 
			imageStyle="width:65rpx;height:65rpx;font-size:15rpx;"
			@click.stop="openSpace"></f-image>
		</view>
		<view class="uni-comment-body" @tap.stop="reply">
			<view class="uni-comment-top"><text>{{item.username}}</text>
			</view>
			<view class="uni-comment-content">{{item.data}}</view>
			<view class="uni-comment-date">
				<view>{{item.time}}</view>
			</view>
		</view>
	</view>
</template>

<script>
	import fImage from '@/components/common/f-image.vue';
	export default {
		components: {
			fImage
		},
		props:{
			item:Object,
			index:Number
		},
		methods: {
			reply() {
				this.$emit('reply',this.item.id)
			},
			openSpace(){
				uni.navigateTo({
					url: '../../pages/user-space/user-space?userid='+this.item.userid
				});
			},
		},
	}
</script>

<style scoped>
.u-comment-list-child{
	padding: 20upx;
	background: #F4F4F4;
	border-bottom: 1upx solid #EEEEEE;
	box-sizing: border-box;
	margin: 0;
	margin-left: 70upx;
	width: auto;
}
</style>
