<template>
	<view>
		<!-- 自定义导航栏 -->
		<uni-nav-bar :fixed="false" :statusBar="true" @click-right="openAdd">
			<block slot="left">
				<view class="nav-left">
					<view class="icon iconfont icon-qiandao"></view>
				</view>
			</block>

			<view class="nav-tab-bar u-f-ajc">
				<!-- <block v-for="(tabBar, index) in tabBars" :key="tabBar.id">
					<view class="u-f-ajc" :class="{'active': tabIndex == index}" @tap="tabClick(index)">
						{{ tabBar.name }}
						<view class="nav-tab-bar-line" v-if="tabIndex == index"></view>
					</view>
				</block> -->
				<swiper-tab-head :tabBars="tabBars" @tabSelect="tabSelect" :currentIndex="tabIndex" :layoutType="1" :showBottomLine="true"></swiper-tab-head>
			</view>
			
			<block slot="right">
				<view class="nav-right">
					<view class="icon iconfont icon-bianji1"></view>
				</view>
			</block>

		</uni-nav-bar>
		
		
		<!-- 列表 -->
		<block v-for="(item, index) in list" :key="index">
			<common-list :item="item" :index="index"></common-list>
		</block>
		
	</view>
</template>

<script>
	import uniNavBar from '../../components/uni-nav-bar/uni-nav-bar.vue';
	import commonList from '../../components/common/common-list.vue';
	import swiperTabHead from '../../components/index/swiper-tab-head.vue'
	
	export default {
		components: {
			uniNavBar,
			commonList,
			swiperTabHead
		},
		data() {
			return {
				tabIndex: 0,
				tabBars: [{
						name: "关注",
						id: 0
					},
					{
						name: "话题",
						id: 1
					}
				],
				list:[
						// 文字
						{
							userpic:"../../static/demo/userpic/1.jpg",
							username:"哈222哈",
							sex:0, //0 男 1 女
							age:26,
							isguanzhu:false,
							title:"我是标题11",
							titlepic:"../../static/demo/datapic/1.jpg",
							video:false,
							share:false,
							path:"深圳 龙岗",
							sharenum:20,
							commentnum:30,
							goodnum:20,
							showtype: 0
						},
						// 图文
						{
							userpic:"../../static/demo/userpic/2.jpg",
							username:"哈111哈",
							sex:0, //0 男 1 女
							age:22,
							isguanzhu:false,
							title:"我是标题333",
							titlepic:"../../static/demo/datapic/2.jpg",
							video:false,
							share:false,
							path:"深圳 龙岗",
							sharenum:20,
							commentnum:30,
							goodnum:20,
							showtype: 1
						},
						// 视频
						{
							userpic:"../../static/demo/userpic/3.jpg",
							username:"哈哈111",
							sex:0, //0 男 1 女
							age:20,
							isguanzhu:false,
							title:"我是标题5555",
							titlepic:"../../static/demo/datapic/3.jpg",
							video:{
								looknum:"20w",
								long:"2:47"
							},
							share:false,
							path:"深圳 龙岗",
							sharenum:20,
							commentnum:30,
							goodnum:20,
							showtype: 0
						},
						// 分享
						{
							userpic:"../../static/demo/userpic/4.jpg",
							username:"哈abc",
							sex:0, //0 男 1 女
							age:25,
							isguanzhu:false,
							title:"我是标题",
							titlepic:"../../static/demo/datapic/4.jpg",
							video:false,
							share:{
								title:"我是分享的标题",
								titlepic:"../../static/demo/datapic/4.jpg"
							},
							path:"深圳 龙岗",
							sharenum:20,
							commentnum:30,
							goodnum:20,
							showtype: 1
						},
					]
				
			}
		},
		methods: {
			openAdd() {

			},
			tabSelect(index) {
				this.tabIndex = index;
			}
		}
	}
</script>

<style>
	
	.nav-left>view,
	.nav-right>view {
		font-size: 40upx;
	}

	.nav-left>view {
		color: #FEAD00;
	}

	.nav-right>view {
		color: #333333;
	}

	.nav-left {
		margin-left: 16upx;
	}

	.nav-right {
		/* margin-right: -50upx; */
	}

	.nav-tab-bar {
		width: 100%;
		/* margin-left: -20upx;
		position: relative; */
	}

	
</style>
