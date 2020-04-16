<template>
	<view class="flex align-center p-3 border-bottom border-light-secondary animated faster fadeIn">
		<f-image :src="userinfo.userpic"
		errorText="失败"
		imageClass="rounded-circle mr-2" 
		imageStyle="width:180rpx;height:180rpx;font-size:15rpx;"
		></f-image>
		<view class="flex-1 flex-column pl-3">
			<view class="flex">
				<view v-for="(item,index) in spacedata" :key="index"
				class="flex flex-column justify-center align-center flex-1">
					<text class="font-lg line-h-md font-weight-bold">
						{{item.num}}
					</text>
					<text class="font">{{item.name}}</text>
				</view>
				
			</view>
			<view class="py-2 px-3">
				<button v-if="!userinfo.isme" type="default" style="width: 100%;" 
				size="mini" @tap.stop="guanzhu"
				:class="getGuanZhuClass">
				{{userinfo.isguanzhu?'已关注':'关注'}}</button>
				<navigator v-if="userinfo.isme" url="/pages/user-set-userinfo/user-set-userinfo" hover-class="none">
					<button type="default"
					:plain="true"
					style="width: 100%;"
					size="mini" class="main-color main-border-color">
						编辑资料
					</button>
				</navigator>
				
			</view>
		</view>
	</view>
	<!-- <view class="user-space-head u-f-ajc">
		<image :src="getBgImg" mode="widthFix" lazy-load @tap.stop="changBgImg"></image>
		<view class="user-space-head-info u-f-ajc u-f-column">
			<image
			:src="userinfo.userpic ? userinfo.userpic:'/static/default.jpg'"
			lazy-load
			style="width: 120rpx;height: 120rpx;"></image>
			<view class="user-space-margin u-f-ac">
				{{userinfo.username}} 
				<tag-sex-age :sex="getSex" :age="getAge"></tag-sex-age> 
			</view>
			<view v-if="!userinfo.isme" class="icon iconfont user-space-head-btn user-space-margin" :class="getGuanZhuClass" @tap.stop="guanzhu">
				{{userinfo.isguanzhu?'已关注':'关注'}}
			</view>
		</view>
	</view> -->
</template>

<script>
	import tagSexAge from "../common/tag-sex-age.vue";
	import fImage from '@/components/common/f-image.vue';
	export default {
		components:{
			tagSexAge,
			fImage
		},
		props:{
			userinfo:Object,
			spacedata:Array
		},
		computed:{
			getSex(){
				return this.userinfo.sex;
			},
			getAge(){
				return this.userinfo.age;
			},
			getBgImg(){
				return "../../static/bgimg/"+this.userinfo.bgimg+".jpg";
			},
			getGuanZhuClass(){
				return !this.userinfo.isguanzhu?'main-bg-color text-white':'';
			}
		},
		methods:{
			// 切换背景
			changBgImg(){
				let no = parseInt(this.userinfo.bgimg);
				this.userinfo.bgimg = no<4 ? ++no : 1;
			},
			// 关注
			async guanzhu(){
				try{
					let url = this.userinfo.isguanzhu ? '/unfollow' : '/follow';
					uni.showLoading({ title: 'loading...', mask: false });
					let [err,res] = await this.$http.post(url,{
						follow_id:this.userinfo.id
					},{
						token:true,
						checkToken:true,
						checkAuth:true
					});
					// 错误处理
					if (!this.$http.errorCheck(err,res)){
						return uni.hideLoading();
					}
					// 成功
					uni.hideLoading();
					uni.showToast({ 
						title: this.userinfo.isguanzhu ? '取消关注成功' : '关注成功' ,
					});
					// 通知父组件修改状态
					this.$emit('update',!this.userinfo.isguanzhu);
				}catch(e){
					return;
				}
				
			}
		}
	}
</script>

<style scoped>
.user-space-head{
	position: relative;
	height: 500upx;
	overflow: hidden;
}
.user-space-head>image{
	width: 100%;
}
.user-space-head-info{
	position: absolute;
	top: 150upx;
}
.user-space-head-info>image{
	width: 150upx;
	height: 150upx;
	border-radius: 100%;
}
.user-space-head-info>view:first-of-type{
	color: #FFFFFF;
	font-size: 35upx;
	font-weight: bold;
	text-shadow: 2upx 2upx 10upx #333333;
}
.user-space-head-btn{
	background: #FFE933;
	color: #333333;
	border: 1upx solid #FFE933;
	padding: 0 15upx;
	border-radius: 10upx;
	font-size: 28upx;
}
.active{
	background:none;
	color: #FFFFFF;
	border: 1upx solid #FFFFFF;
}
</style>
