<template>
	<view class="uni-page-body">
		<!-- 头部面板 -->
		<user-space-header></user-space-header>

		<view class="home-tabs-info u-p-r">
			<home-tabs :numbers="numbers"></home-tabs>
		</view>

		<view class="user-space-segmentation"></view>

		<swiper-tab-head :tabBars="tabBars" :layoutType="2" :currentIndex="tabIndex" @tabSelect="tabSelect"></swiper-tab-head>

		<template v-if="tabIndex===0">
			<user-space-userinfo></user-space-userinfo>
		</template>

		<template v-else-if="tabIndex===1">
			<block v-for="(item, index) in list" :key="index">
				<common-list :item="item" :index="index"></common-list>
			</block>
		</template>

	</view>
</template>

<script>
	import userSpaceHeader from '../../components/user-space/user-space-header.vue';
	import homeTabs from '../../components/home/home-tabs.vue';
	import swiperTabHead from '../../components/index/swiper-tab-head.vue';
	import tagSexNumber from '../../components/common/tag-sex-number.vue';
	import userSpaceUserinfo from '../../components/user-space/user-space-userinfo.vue';
	import commonList from '../../components/common/common-list.vue';

	export default {
		components: {
			homeTabs,
			swiperTabHead,
			tagSexNumber,
			userSpaceUserinfo,
			userSpaceHeader,
			commonList,
		},
		data() {
			return {
				tabIndex: 0,
				scrollLeft: 0,
				TabCur: 0,
				itemWidth: 0,
				numbers: [{
						title: "获赞",
						number: 37
					},
					{
						title: "动态",
						number: 46
					},
					{
						title: "评论",
						number: 12
					}
				],
				tabBars: [{
						name: "主页",
						id: "guanzhu"
					},
					{
						name: "帖子",
						id: "tuijian"
					},
					{
						name: "动态",
						id: "tiyu"
					}
				],
				list: [
					// 文字
					{
						userpic: "../../static/demo/userpic/1.jpg",
						username: "哈222哈",
						sex: 0, //0 男 1 女
						age: 26,
						isguanzhu: false,
						title: "我是标题11",
						titlepic: "../../static/demo/datapic/1.jpg",
						video: false,
						share: false,
						path: "深圳 龙岗",
						sharenum: 20,
						commentnum: 30,
						goodnum: 20,
						showtype: 0
					},
					// 图文
					{
						userpic: "../../static/demo/userpic/2.jpg",
						username: "哈111哈",
						sex: 0, //0 男 1 女
						age: 22,
						isguanzhu: false,
						title: "我是标题333",
						titlepic: "../../static/demo/datapic/2.jpg",
						video: false,
						share: false,
						path: "深圳 龙岗",
						sharenum: 20,
						commentnum: 30,
						goodnum: 20,
						showtype: 1
					},
					// 视频
					{
						userpic: "../../static/demo/userpic/3.jpg",
						username: "哈哈111",
						sex: 0, //0 男 1 女
						age: 20,
						isguanzhu: false,
						title: "我是标题5555",
						titlepic: "../../static/demo/datapic/3.jpg",
						video: {
							looknum: "20w",
							long: "2:47"
						},
						share: false,
						path: "深圳 龙岗",
						sharenum: 20,
						commentnum: 30,
						goodnum: 20,
						showtype: 0
					},
					// 分享
					{
						userpic: "../../static/demo/userpic/4.jpg",
						username: "哈abc",
						sex: 0, //0 男 1 女
						age: 25,
						isguanzhu: false,
						title: "我是标题",
						titlepic: "../../static/demo/datapic/4.jpg",
						video: false,
						share: {
							title: "我是分享的标题",
							titlepic: "../../static/demo/datapic/4.jpg"
						},
						path: "深圳 龙岗",
						sharenum: 20,
						commentnum: 30,
						goodnum: 20,
						showtype: 1
					}
				]
			}
		},
		onNavigationBarButtonTap() {
			
		},
		methods: {
			/* tab item 点击 */
			tabSelect(index) {
				this.tabIndex = index;
				
			}

		}
	}
</script>

<style>
	.home-tabs-info {
		border-radius: 20upx 20upx 0 0;
		z-index: 10;
		margin-top: -20upx;
		/* border-top-left-radius: 20upx;
		border-top-right-radius: 20upx; */
	}

	.user-space-segmentation {
		background-color: #F4F4F4;
		height: 20upx;
	}
</style>
