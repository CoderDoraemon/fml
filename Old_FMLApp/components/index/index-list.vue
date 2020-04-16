<template>
	<view class="index-list animated fadeIn fast">
		<view class="index-list1 u-f-ac u-f-jsb">
			<view class="u-f-ac text-dark">
				<f-image :src="item.userpic" 
				errorText="失败"
				imageClass="rounded-circle mr-2" 
				imageStyle="width:65rpx;height:65rpx;font-size:15rpx;"
				@click.stop="openSpace"></f-image>
				<view>
					<view class="line-h-sm">{{item.username}}</view>
					<view class="text-light-muted font-sm">
					{{item.create_time|formatTime}}</view>
				</view>
			</view>
			<view class="u-f-ac main-bg-color text-white px-2 rounded  animated faster" hover-class="pulse" v-show="!item.isguanzhu" @tap="guanzhu">
				关注
			</view>
		</view>
		<view class="index-list2" @tap="opendetail">{{item.title}}</view>
		<view class="index-list3 u-f-ajc" @tap="opendetail">
			<template v-if="item.titlepic">
				<!-- 图片 -->
				<f-image :src="item.titlepic" mode="aspectFill"></f-image>
			</template>
			<!-- 视频 -->
			<template v-if="item.type=='video'">
				<view class="icon iconfont icon-bofang index-list-play"></view>
				<view class="index-list-playinfo">
					{{item.playnum}}次播放 {{item.long}}
				</view>
			</template>
		</view>
		<view class="u-f-ac mt-1">
			<view class="u-f-ajc u-f1 py-1 animated faster" 
			hover-class="main-color pulse"
			:class="item.infonum.index===1?'index-list-active':''" @tap="caozuo('ding')">
				<text class="iconfont icon-dianzan2 pr-2 font-lg"></text>
				{{item.infonum.dingnum > 0 ? item.infonum.dingnum : '顶'}}
			</view>
			<view class="u-f-ajc u-f1 py-1 animated faster" 
			hover-class="main-color pulse"
			:class="item.infonum.index===2?'index-list-active':''" @tap="caozuo('cai')">
				<text class="iconfont icon-cai pr-2 font-lg"></text>
				{{item.infonum.cainum > 0 ? item.infonum.cainum : '踩'}}
			</view>
			<view class="u-f-ajc u-f1 py-1 animated faster" 
			hover-class="main-color pulse" @tap="opendetail">
				<text class="iconfont icon-pinglun2 pr-2 font-lg"></text>
				{{item.commentnum > 0 ? item.commentnum : '评论'}}
			</view>
			<view class="u-f-ajc u-f1 py-1 animated faster" 
			hover-class="main-color pulse" @tap="opendetail">
				<text class="iconfont icon-zhuanfa1 pr-2 font-lg"></text>
				{{item.sharenum > 0 ? item.sharenum : '分享'}}
			</view>
		</view>
	</view>
</template>

<script>
	import $T from "@/common/time.js"
	import fImage from '@/components/common/f-image.vue';
	export default {
		components: {
			fImage
		},
		props:{
			item:Object,
			index:Number
		},
		filters:{
			formatTime(val){
				return $T.gettime.gettime(val)
			}
		},
		methods:{
			openSpace(){
				uni.navigateTo({
					url:"../../pages/user-space/user-space?userid="+this.item.userid
				})
			},
			// 关注
			async guanzhu(){
				try{
					let [err,res] = await this.$http.post('/follow',{
						follow_id:this.item.userid
					},{
						token:true,
						checkToken:true,
						checkAuth:true
					});
					// 错误处理
					if (!this.$http.errorCheck(err,res)){
						return;
					}
					// 通知首页修改数据
					uni.showToast({ title: '关注成功' });
					let resdata = {
					 	type:"guanzhu",
					 	userid:this.item.userid,
					 	data:true
					};
					// 通知父组件
					this.$emit('changeevent',resdata);
					// 通知首页
					uni.$emit('updateData',resdata);
				}catch(e){ return; }
			},
			// 顶踩
			async caozuo(type){
				try{
					let index = (type === 'ding') ? 1 : 2; // 操作后的状态
					if(this.item.infonum.index === index) return; // 状态相同不修改
					let [err,res] = await this.$http.post('/support',{
						post_id:this.item.id,
						type:index-1
					},{
						token:true,
						checkToken:true,
						checkAuth:true
					});
					// 错误处理
					if (!this.$http.errorCheck(err,res)) return;
					uni.showToast({
						title: index == 1 ? "顶成功" : "踩成功"
					});
					let resdata = {
						type:"support",
						post_id:this.item.id,
						do:type
					};
					// 通知父组件
					this.$emit('changeevent',resdata);
					// 通知全局
					uni.$emit("updateData",resdata);
				}catch(e){ return; }
			},
			// 进入详情页
			opendetail(){
				uni.navigateTo({
					url: '../../pages/detail/detail?detailData='+JSON.stringify(this.item),
				});
				this.User.addHistoryList(this.item);
			}
		}
	}
</script>

<style scoped>
.index-list{
	padding: 20upx;
}
.index-list1>view:first-child{
	color: #999999;
}
.index-list2{
	padding-top: 15upx;
	font-size: 32upx;
}
.index-list3{
	position: relative;
	padding-top: 15upx;
}
.index-list3>image{
	width: 100%;
}
.index-list4 view{
	color: #999999;
}
.index-list4{
	padding: 15upx 0;
}
.index-list4>view>view>view,.index-list4>view>view:first-child{
	margin-right: 10upx;
}
.index-list-play{
	position: absolute;
	font-size: 140upx;
	color: #FFFFFF;
}
.index-list-playinfo{
	position: absolute;
	background: rgba(51, 51, 51, 0.72);
	color: #FFFFFF;
	bottom: 8upx;
	right: 8upx;
	border-radius: 40upx;
	font-size: 22upx;
	padding: 0 12upx;
}
.index-list-active{
	color: #FD597C!important;
}
</style>
