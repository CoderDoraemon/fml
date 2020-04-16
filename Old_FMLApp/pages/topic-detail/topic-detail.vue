<template>
	<view>
		<!-- 话题介绍 -->
		<topic-info :item="topicInfo"></topic-info>
		<!-- 精品贴 -->
		<divider></divider>
		<view class="border-bottom px-3 py-2 flex align-center" 
		hover-class="bg-light-secondary">
			<image src="/static/common/totop.jpg" style="width: 25rpx;height: 25rpx;" class="mr-2"></image>
			<text class="font-md text-ellipsis">【新人必读】uni-app实战第二季商城类app开发</text>
		</view>
		<view class="border-bottom px-3 py-2 flex align-center"
		hover-class="bg-light-secondary">
			<image src="/static/common/totop.jpg" style="width: 25rpx;height: 25rpx;" class="mr-2"></image>
			<text class="font-md text-ellipsis">【话题头条】uni-app实战第二季商城类app开发</text>
		</view>
		<divider></divider>
		<!-- tabbar切换 -->
		<swiper-tab-head 
		:tabBars="tabBars" 
		:tabIndex="tabIndex"
		@tabtap="tabtap"
		scrollItemStyle="width:50%;"
		scrollStyle="border-bottom:0;">
		</swiper-tab-head>
		<!-- 列表 -->
		<view class="topic-detail-list">
			<block v-for="(item,index) in tablist" :key="index">
				<template v-if="tabIndex==index">
					<!-- 列表 -->
					<template v-if="item.list.length > 0">
						<block v-for="(list,listindex) in item.list" 
						:key="listindex">
							<common-list @changeevent="updateData" 
							:item="list" :index="listindex"></common-list>
							<divider></divider>
						</block>
						<!-- 上拉加载 -->
						<load-more :loadtext="item.loadtext"></load-more>
					</template>
					<template v-else-if="!item.firstload">
						<view style="font-size: 50upx;font-weight: bold;color: #CCCCCC;padding-top: 100upx;" class="u-f-ajc">Loading ...</view>
					</template>
					<template v-else>
						<!-- 无内容默认 -->
						<no-thing :position="false"></no-thing>
					</template>
				</template>
			</block>
		</view>
		
		
		<!-- 发布按钮 -->
		<view class="main-bg-color text-white animated faster rounded-circle flex justify-center align-center add-btn" hover-class="pulse">
			<text class="iconfont icon-zengjia" style="font-size: 50rpx;"></text>
		</view>
		
	</view>
</template>

<script>
	import topicInfo from "../../components/topic/topic-info.vue";
	import swiperTabHead from "../../components/index/swiper-tab-head.vue";
	import commonList from "../../components/common/common-list.vue";
	import loadMore from "../../components/common/load-more.vue";
	import noThing from "../../components/common/no-thing.vue";
	export default {
		components:{
			topicInfo,
			swiperTabHead,
			commonList,
			loadMore,
			noThing,
		},
		data() {
			return {
				topicInfo:{
					titlepic:"../../static/demo/topicpic/13.jpeg",
					title:"忆往事，敬余生",
					desc:"我是描述",
					totalnum:1000,
					todaynum:1000,
				},
				tabIndex:0,
				tabBars:[
					{ name:"默认",id:"moren" },
					{ name:"最新",id:"zuixin" },
				],
				tablist:[
					{ loadtext:"上拉加载更多",list:[],firstload:false,page:1},
					{ loadtext:"上拉加载更多",list:[],firstload:false,page:1},
				]
			};
		},
		// 上拉触底事件
		onReachBottom() {
			// 上拉加载
			this.loadmore();
		},
		// 监听下拉刷新 
		onPullDownRefresh(){
			this.getList();
		},
		onLoad(e) {
			this.__init(JSON.parse(e.detail));
			// 开启监听
			uni.$on('updateData',this.updateData);
		},
		methods:{
			updateData(data){
				switch (data.type){
					case "guanzhu":
					this.updateGuanZhu(data)
						break;
					case "support":
					this.updateSupport(data);
						break;
					case 'updateComment':
					this.updateComment(data);
						break;
				}
			},
			// 更新评论数
			updateComment(data){
				// 拿到当前对象
				let obj = this.tablist[this.tabIndex].list.find(value =>{
					return value.id === data.post_id;
				});
				if (!obj) return;
				obj.commentnum++; // 评论数+1
			},
			// 更新关注信息
			updateGuanZhu(data){
				this.tablist[this.tabIndex].list.forEach((item,index)=>{
					if (item.userid === data.userid) {
						item.isguanzhu = data.data;
					}
				})
			},
			updateSupport(data){
				let obj = this.tablist[this.tabIndex].list.find((item)=>{
					return item.id === data.post_id;
				})
				if(!obj) return;
				let oldindex = obj.infonum.index; // 操作前的状态
				obj.infonum.index = (data.do == 'ding') ? 1 : 2; // 操作后的状态
				if (oldindex !== 0) { //之前操作过
					oldindex == 1 ? obj.infonum.dingnum-- : obj.infonum.cainum--;
				}
				if (obj.infonum.index !== 0) {  // 当前操作
					obj.infonum.index == 1 
						? obj.infonum.dingnum++ : obj.infonum.cainum++;
				}
			},
			// 初始化
			__init(obj){
				// 修改标题
				uni.setNavigationBarTitle({ title: obj.title });
				this.topicInfo = obj;
				// 获取列表数据
				this.getList();
			},
			// 获取数据
			async getList(){
				let url = `/topic/${this.topicInfo.id}/post/${this.tablist[this.tabIndex].page}`;
				let [err,res] = await this.$http.get(url,{},{token:true});
				// 错误处理
				if (!this.$http.errorCheck(err,res)) {
					return this.tablist[this.tabIndex].loadtext="上拉加载更多";
				}
				let arr = [];
				let list = res.data.data.list;
				for (let i = 0; i < list.length; i++) {
					arr.push(this.__format(list[i]));
				}
				this.tablist[this.tabIndex].list = this.tablist[this.tabIndex].page > 1 ? this.tablist[this.tabIndex].list.concat(arr) : arr;
				this.tablist[this.tabIndex].firstload = true;
				uni.stopPullDownRefresh();
				return	this.tablist[this.tabIndex].loadtext=(list.length < 10) ?"没有更多数据了" : "上拉加载更多";
			},
			// 转换格式
			__format(item){
				return {
					userid:item.user.id,
					userpic:item.user.userpic,
					username:item.user.username,
					isguanzhu:!!item.user.fens.length,
					id:item.id,
					title:item.title,
					type:"img", // img:图文,video:视频
					titlepic:item.titlepic,
					video:false,
					path:item.path,
					share:!!item.share,
					infonum:{
						index:(item.support.length>0) ? (item.support[0].type+1) : 0,
						dingnum:item.ding_count,
						cainum:item.cai_count,
					},
					goodnum:item.ding_count,
					commentnum:item.comment_count,
					sharenum:item.sharenum,
					sex:item.user.userinfo.sex,
					age:item.user.userinfo.age,
					create_time:item.create_time
				}
			},
			// 上拉加载
			loadmore(){
				if(this.tablist[this.tabIndex].loadtext!="上拉加载更多") return;
				// 修改状态
				this.tablist[this.tabIndex].loadtext="加载中...";
				// 页数+1
				this.tablist[this.tabIndex].page++;
				// 获取数据
				this.getList();
			},
			// tabbar点击事件
			tabtap(index){
				this.tabIndex=index;
				this.tablist[this.tabIndex].page = 1;
				this.getList();
			},
		}
	}
</script>

<style>
.add-btn{
	position: fixed;z-index: 100;right: 35rpx;bottom: 35rpx;width: 120rpx;height: 120rpx;
}
</style>
