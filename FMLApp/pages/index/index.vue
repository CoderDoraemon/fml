<template>
	<view>
		
		<!-- <swiper-tab-head 
		:tabBars="tabBars" 
		:tabIndex="tabIndex" 
		@tabtap="tabtap"
		:itemWidth="itemWidth">
		</swiper-tab-head> -->
		
		<swiper-tab-head :tabBars="tabBars" @tabSelect="tabSelect" :currentIndex="tabIndex"></swiper-tab-head>
		
		<view class="uni-tab-bar">
			<swiper class="swiper-box" 
			:style="{height: swiperheight+'px'}" 
			:current="tabIndex" 
			@change="tabChange">
				<swiper-item v-for="(items, index) in newslist" :key="index">
					<scroll-view scroll-y class="list" @scrolltolower="loadMore(index)">
						<block v-for="(item, row) in items.list" :key="row">
							<index-list :item="item" @toUserSpace="toUserSpace(index)"></index-list>
						</block>
						
						<load-more :loadtext="items.loadtext"></load-more>
						
					</scroll-view>
				</swiper-item>
			</swiper>
		</view>
		
	</view>
</template>

<script>
	import indexList from '../../components/index/index-list.vue'
	import swiperTabHead from '../../components/index/swiper-tab-head.vue'
	import loadMore from '../../components/common/load-more.vue';
	export default {
		components: {
			indexList,
			swiperTabHead,
			loadMore
		},
		data() {
			return {
				swiperheight: 500,
				tabIndex: 0,
				itemWidth: 150,
				tabBars: [{
						name: "关注",
						id: "guanzhu"
					},
					{
						name: "推荐",
						id: "tuijian"
					},
					{
						name: "体育",
						id: "tiyu"
					}
				],
				newslist: [{
							"loadtext": "上拉加载更多",
						list: [{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: false,
								title: "我是标题",
								type: "img", // img:图文,video:视频
								titlepic: "../../static/demo/datapic/11.jpg",
								infonum: {
									index: 0, //0:没有操作，1:顶,2:踩；
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							},
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: true,
								title: "我是标题",
								type: "video", // img:图文,video:视频
								titlepic: "../../static/demo/datapic/11.jpg",
								playnum: "20w",
								long: "2:47",
								infonum: {
									index: 1, //0:没有操作，1:顶,2:踩；
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							}
						]
					},
					{
							"loadtext": "上拉加载更多",
						list: [{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: false,
								title: "我是标题",
								type: "img", // img:图文,video:视频
								titlepic: "../../static/demo/datapic/11.jpg",
								infonum: {
									index: 0, //0:没有操作，1:顶,2:踩；
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							},
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: true,
								title: "我是标题",
								type: "video", // img:图文,video:视频
								titlepic: "../../static/demo/datapic/11.jpg",
								playnum: "20w",
								long: "2:47",
								infonum: {
									index: 1, //0:没有操作，1:顶,2:踩；
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							},
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: false,
								title: "我是标题",
								type: "img", // img:图文,video:视频
								titlepic: "../../static/demo/datapic/11.jpg",
								infonum: {
									index: 0, //0:没有操作，1:顶,2:踩；
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							},
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: true,
								title: "我是标题",
								type: "video", // img:图文,video:视频
								titlepic: "../../static/demo/datapic/11.jpg",
								playnum: "20w",
								long: "2:47",
								infonum: {
									index: 1, //0:没有操作，1:顶,2:踩；
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							}
						]
					},
					{
							"loadtext": "上拉加载更多",
						list: [{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: false,
								title: "我是标题",
								type: "img", // img:图文,video:视频
								titlepic: "../../static/demo/datapic/11.jpg",
								infonum: {
									index: 0, //0:没有操作，1:顶,2:踩；
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							},
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: true,
								title: "我是标题",
								type: "video", // img:图文,video:视频
								titlepic: "../../static/demo/datapic/11.jpg",
								playnum: "20w",
								long: "2:47",
								infonum: {
									index: 1, //0:没有操作，1:顶,2:踩；
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							},
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: false,
								title: "我是标题",
								type: "img", // img:图文,video:视频
								titlepic: "../../static/demo/datapic/11.jpg",
								infonum: {
									index: 0, //0:没有操作，1:顶,2:踩；
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							},
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: true,
								title: "我是标题",
								type: "video", // img:图文,video:视频
								titlepic: "../../static/demo/datapic/11.jpg",
								playnum: "20w",
								long: "2:47",
								infonum: {
									index: 1, //0:没有操作，1:顶,2:踩；
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							}
						]
					}
				]
			}
		},
		onLoad() {
			uni.getSystemInfo({
				success: (res) => {
					let height = res.windowHeight - uni.upx2px(100)
					this.swiperheight = height;
					// this.itemWidth = res.windowWidth / this.tabBars.length
				}
			})
		},
		/* 导航栏按钮点击 */
		onNavigationBarButtonTap(e) {
			switch (e.index){
				case 1:
				uni.navigateTo({
					url: '../publish/publish'
				})
					break;
				default:
					break;
			}
		},
		/* 搜索框点击 */
		onNavigationBarSearchInputClicked(e) {
			console.log(JSON.stringify(e))
			uni.navigateTo({
				url: '../search/search'
			})
		},
		methods: {
			// 跳转到个人空间
			toUserSpace(index) {
				uni.navigateTo({
					url: "../user-space/user-space"
				});
			},
			/* tab item 点击 */
			tabSelect(index) {
				console.log("点击" + index)
				this.tabIndex = index;
			},
			tabChange(e) {
				this.tabIndex = e.detail.current;
			},
			loadMore(index) {
				
				if (this.newslist[index].loadtext == "上拉加载更多") {
					
					this.newslist[index].loadtext = "加载中";
					
					setTimeout(()=> {
						
						let obj = {
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: false,
								title: "我是标题",
								type: "img", // img:图文,video:视频
								titlepic: "../../static/demo/datapic/11.jpg",
								infonum: {
									index: 0, //0:没有操作，1:顶,2:踩；
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							};
							
							this.newslist[index].list.push(obj);
							
							this.newslist[index].loadtext = "上拉加载更多";
						
					}, 1000);
					
				}
				
			}
		}
	}
</script>

<style>
	

</style>
