<template>
	<view class="paper-list u-f-ac animated fadeIn fast" @tap="opendetail">
		<f-image :src="item.userpic"
		errorText="失败"
		imageClass="rounded-circle mr-2" 
		imageStyle="width:80rpx;height:80rpx;font-size:15rpx;"
		@click.stop="openSpace"></f-image>
		<view>
			<view class="u-f-ac u-f-jsb">
				{{item.username}} 
				<view class="text-light-muted">{{item.time}}</view>
			</view>
			<view class="u-f-ac u-f-jsb main-light-dark">{{item.data}}
			<template v-if="item.noreadnum>0">
				<uni-badge :text="getItemNoreadnum" type="error"></uni-badge>
			</template>
			</view>
		</view>
	</view>
</template>

<script>
	import uniBadge from "@/components/uni-badge/uni-badge.vue";
	import fImage from '@/components/common/f-image.vue';
	export default {
		components:{
			uniBadge,
			fImage
		},
		props:{
			item:Object,
			index:Number
		},
		computed: {
			getItemNoreadnum() {
				return this.item.noreadnum
			}
		},
		methods:{
			opendetail(){
				let obj = {
					userid:this.item.userid,
					username:this.item.username,
					userpic:this.item.userpic
				};
				this.User.navigate({
					url: '../../pages/user-chat/user-chat?userinfo='+JSON.stringify(obj),
				});
				// 更新未读数的状态
				this.$chat.Read(this.item)
			}
		}
	}
</script>

<style scoped>
.paper-list{
	border-bottom: 1upx solid #EBE9E7;
	padding: 20upx 0;
}
.paper-list>view{
	flex: 1;
}
.paper-list>view>view:first-child{
	font-size: 35upx;
}
</style>
