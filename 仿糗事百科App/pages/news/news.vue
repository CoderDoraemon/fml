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
				<block v-for="(tabBar, index) in tabBars" :key="tabBar.id">
					<view class="u-f-ajc" :class="{'active': tabIndex == index}" @tap="tabClick(index)">
						{{ tabBar.name }}
						<view class="nav-tab-bar-line" v-if="tabIndex == index"></view>
					</view>
				</block>
			</view>

			<block slot="right">
				<view class="nav-right">
					<view class="icon iconfont icon-bianji1"></view>
				</view>
			</block>

		</uni-nav-bar>
		
		<!-- 列表 -->
		<view class="comment-list u-f">
			<!-- 左边信息 -->
			<view class="comment-list-l">
				<image src="../../static/demo/userpic/10.jpg" mode="widthFix"></image>
			</view>

			<!-- 右边信息 -->
			<view class="comment-list-r u-f-column">
				<view class="u-f u-f-jsb">
					<view class="u-f-ajc">
						<view class="">三余先生</view>
						<view class="user-sex icon iconfont icon-nan">25</view>
					</view>
					<view class="u-f-ajc">
						<view class="user-attention icon iconfont icon-zengjia">关注</view>
						<view class="icon iconfont icon-guanbi"></view>
					</view>
				</view>
				<view class="u-f1">
					六道快手家常菜六道快手家常菜六道快手家常菜六道快手家常菜六道快手家常菜六道快手家常菜六道快手家常菜六道快手家常菜六道快手家常菜六道快手家常菜六道快手家常菜六道快手家常菜六道快手家常菜六道快手家常菜
				</view>
				<view class="u-f-ajc">
					<image src="../../static/demo/banner2.jpg" mode="widthFix" lazy-load></image>
					<view class="comment-list-play icon iconfont icon-bofang"></view>
					<view class="comment-list-playInfo">
						20w 次播放2：47
					</view>
				</view>
				<view class="u-f u-f-jsb">
					<view class="">深圳 龙感湖</view>
					<view class="u-f-ajc">
						<view class="icon iconfont icon-zhuanfa">36</view>
						<view class="icon iconfont icon-pinglun1">36</view>
						<view class="icon iconfont icon-dianzan1">57</view>
					</view>
				</view>
			</view>

		</view>

	</view>
</template>

<script>
	import uniNavBar from '../../components/uni-nav-bar/uni-nav-bar.vue';
	export default {
		components: {
			uniNavBar
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
				]
			}
		},
		methods: {
			openAdd() {

			},
			tabClick(index) {
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
		margin-left: -20upx;
		position: relative;
	}

	.nav-tab-bar>view {
		font-size: 32upx;
		padding: 0 15upx;
		font-weight: bold;
		color: #969696;
	}

	.active {
		color: #333333 !important;
	}

	.nav-tab-bar-line {
		position: absolute;
		border-bottom: 5upx solid #FEDE33;
		border-top: 5upx solid #FEDE33;
		width: 70upx;
		border-radius: 20upx;
		bottom: 8upx;
	}

	.comment-list {
		padding: 20upx;
		border-bottom: 1upx solid #EEEEEE;
	}

	.comment-list-l image {
		width: 90upx;
		height: 90upx;
		border-radius: 100%;
	}

	.comment-list-r {
		margin-left: 12upx;
	}

	.comment-list-r>view:nth-child(1)>view:first-child .user-sex {
		background-color: #4C99FF;
		color: #FFFFFF;
		font-size: 22upx;
		padding: 5upx 15upx;
		line-height: 24upx;
		border-radius: 24upx;
		margin-left: 8upx;
	}

	.comment-list-r>view:nth-child(1)>view:last-child .user-attention {
		background-color: #F3F3F3;
		color: #333333;
		font-size: 22upx;
		padding: 5upx 15upx;
		line-height: 24upx;
		border-radius: 5upx;
		margin-right: 8upx;
	}

	.comment-list-r>view:nth-child(2) {
		margin-bottom: 15upx;
	}
	
	.comment-list-r>view:nth-child(3) image {
		width: 100%;
		border-radius: 10upx;
	}

	.comment-list-r>view:nth-child(3) {
		position: relative;
		margin-bottom: 15upx;
	}
	
	.comment-list-play,
	.comment-list-playInfo {
		position: absolute;
		/* color: #FFFFFF; */
	}

	.comment-list-play {
		/* font-size: 130upx;
		background-color: #007AFF; */
	}

	.comment-list-playInfo {
		right: 8upx;
		bottom: 0;
		color: #FFFFFF;
		background-color: rgba(58, 55, 54, 0.6);
		font-size: 24upx;
		border-radius: 24upx;
		padding: 0 10upx;
	}

	.comment-list-r>view:nth-child(4) {
		color: #C1C1C1;
		font-size: 28upx;
	}

	.comment-list-r>view:nth-child(4)>view:nth-child(2)>view {
		margin-left: 15upx;
		padding-left: 8upx;
	}
</style>
