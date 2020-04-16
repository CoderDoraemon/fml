<template>
	<view class="container">
		<view class="py-2 u-f-ac u-f-jsb">
			<view class="u-f-ac text-dark">
				<f-image :src="item.userpic" 
				errorText="失败"
				imageClass="rounded-circle mr-2" 
				imageStyle="width:65rpx;height:65rpx;font-size:15rpx;"
				@click.stop="openSpace"></f-image>
				<view>
					<view class="line-h-sm u-f-ac">
						<text class="mr-2">{{item.username}}</text>
						<tag-sex-age :sex="getSex" :age="getAge"></tag-sex-age>
					</view>
					<view class="text-light-muted font-sm">
						{{item.create_time|formatTime}}
					</view>
				</view>
			</view>
			<view class="u-f-ac main-bg-color text-white px-2 rounded  animated faster" hover-class="pulse" v-show="!item.isguanzhu" @tap="guanzhu">
				关注
			</view>
		</view>
		<view @tap.stop="opendetail">{{item.title}}</view>
		<view class="u-f-ajc" style="flex-direction: column;" @tap.stop="opendetail">
			<template v-if="item.titlepic">
				<f-image :src="item.titlepic" mode="aspectFill"></f-image>
			</template>
		</view>
		
		<view class="u-f-ac mt-1">
			<view class="u-f-ajc u-f1 py-1 animated faster" 
			hover-class="main-color pulse"
			:class="item.infonum.index===1?'active':''" @tap="caozuo('ding')">
				<text class="iconfont icon-dianzan2 pr-2 font-lg"></text>
				{{item.infonum.dingnum > 0 ? item.infonum.dingnum : '顶'}}
			</view>
			<view class="u-f-ajc u-f1 py-1 animated faster" 
			hover-class="main-color pulse"
			:class="item.infonum.index===2?'active':''" @tap="caozuo('cai')">
				<text class="iconfont icon-cai pr-2 font-lg"></text>
				{{item.infonum.cainum > 0 ? item.infonum.cainum : '踩'}}
			</view>
			<view class="u-f-ajc u-f1 py-1 animated faster" 
			hover-class="main-color pulse" @tap="opendetail">
				<text class="iconfont icon-pinglun2 pr-2 font-lg"></text>
				{{item.commentnum > 0 ? item.commentnum : '评论'}}
			</view>
			<view class="u-f-ajc u-f1 py-1 animated faster" 
			hover-class="main-color pulse"  @tap="opendetail">
				<text class="iconfont icon-zhuanfa1 pr-2 font-lg"></text>
				{{item.sharenum > 0 ? item.sharenum : '分享'}}
			</view>
		</view>
	</view>
</template>

<script>
	import tagSexAge from "./tag-sex-age.vue"
	import $T from "@/common/time.js"
	import fImage from '@/components/common/f-image.vue';
	export default {
		components:{
			tagSexAge,
			fImage
		},
		props:{
			nonavigate:{
				type:Boolean,
				default:false
			},
			item:Object,
			index:Number
		},
		filters:{
			formatTime(val){
				return $T.gettime.gettime(val)
			}
		},
		computed: {
			getSex() {
				return this.item.sex;
			},
			getAge(){
				return this.item.age;
			}
		},
		methods:{
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
					if (!this.$http.errorCheck(err,res)) return;
					// 通知首页修改数据
					uni.showToast({ title: '关注成功' });
					let resdata = {
					 	type:"guanzhu",
					 	userid:this.item.userid,
					 	data:true
					};
					// 通知父组件
					this.$emit('changeevent',resdata);
					// 通知全局
					uni.$emit('updateData',resdata);
				}catch(e){ return; }
			},
			// 进入详情页
			opendetail(){
				uni.navigateTo({
					url: '../../pages/detail/detail?detailData='+JSON.stringify(this.item),
				});
				this.User.addHistoryList(this.item);
			},
			async caozuo(type){
				let index = (type === 'ding') ? 1 : 2; // 当前操作
				let [err,res] = await this.$http.post('/support',{
					post_id:this.item.id,
					type:index-1
				},{
					token:true,
					checkToken:true,
					checkAuth:true
				});
				if (!this.$http.errorCheck(err,res)) return;
				uni.showToast({ title: index == 1 ? "顶成功" : "踩成功" });
				// 通知父组件
				let resdata = {
					type:"support",
					post_id:this.item.id,
					do:type
				};
				this.$emit('changeevent',resdata);
				// 通知全局
				return uni.$emit("updateData",resdata);
			},
			openSpace(){
				if (this.nonavigate) return;
				uni.navigateTo({
					url:"../../pages/user-space/user-space?userid="+this.item.userid
				})
			}
		}
	}
</script>

<style scoped>
@import "../../common/list.css";
.active{
	color: #FD597C!important;
}
</style>
