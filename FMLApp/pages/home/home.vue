<template>
	<view>
		<!-- 未登录 -->
		<template v-if="!loginStatus">
			<view class="u-f-ajc">登陆仿糗事百科，体验更多功能</view>
			<!-- 第三方登陆 -->
			<view class="other-login u-f-ac">
				<view class="u-f-ajc u-f1">
					<view class="icon iconfont icon-weixin u-f-ajc"></view>
				</view>
				<view class="u-f-ajc u-f1">
					<view class="icon iconfont icon-xinlangweibo u-f-ajc"></view>
				</view>
				<view class="u-f-ajc u-f1">
					<view class="icon iconfont icon-QQ u-f-ajc"></view>
				</view>
			</view>
			<!-- 账号密码登陆 -->
			<view class="u-f-ajc">
				账号密码登陆<view class="icon iconfont icon-jinru"></view>
			</view>
		</template>
		
		<template v-else>
			<view class="login-user-info u-f-ac u-f-jsb">
				
				<view class="u-f">
					<image src="../../static/demo/userpic/1.jpg" mode="widthFix" lazy-load></image>
					<view class="u-f-column">
						<text>昵称</text>
						<text>总访客0 今日0</text>
					</view>
				</view>
				
				<view class="login-user-info-arrow icon iconfont icon-jinru"></view>
				
			</view>
		</template>

		<!-- 横向bar -->
		<view class="home-tabs u-f-ajc">
			<view class="u-f-column u-f1 u-f-ajc">
				0<view class="">糗事</view>
			</view>
			<view class="u-f-column u-f1 u-f-ajc">
				0<view class="">动态</view>
			</view>
			<view class="u-f-column u-f1 u-f-ajc">
				0<view class="">评论</view>
			</view>
			<view class="u-f-column u-f1 u-f-ajc">
				0<view class="">收藏</view>
			</view>
		</view>
		<!-- 广告位 -->
		<view class="home-ad u-f-ajc">
			<image src="../../static/demo/banner3.jpg" mode="widthFix" lazy-load></image>
		</view>
		<!-- 列表 -->
		<view class="home-list">
			<block v-for="(item,index) in list" :key="index">
				<home-list-item :item="item" :index="index"></home-list-item>
			</block>
		</view>

	</view>
</template>

<script>
	export default {
		components: {},
		data() {
			return {
				loginStatus:true,
				homeinfo:{
					userpic:"../../static/demo/userpic/11.jpg",
					username:"昵称",
					totalnum:0,
					todaynum:0,
				},
				homedata:[
					{ name:"糗事", num:0 },
					{ name:"动态", num:0 },
					{ name:"评论", num:0 },
					{ name:"粉丝", num:0 },
				],
				list:[
					{ icon:"liulan",name:"浏览历史",clicktype:"navigateTo",url:"/pages/user-history/user-history"},
					{ icon:"huiyuanvip",name:"糗百认证",clicktype:"nothing",url:"" },
					{ icon:"keyboard",name:"审核糗事",clicktype:"nothing",url:"" },
				]
			}
		},
		onNavigationBarButtonTap() {
			uni.navigateTo({
				url: '../setter/setter'
			});
		},
		methods: {
			
		}
	}
</script>

<style>
	.other-login, .login-user-info {
		padding: 20upx;
	}

	.other-login>view>view {
		width: 100upx;
		height: 100upx;
		border-radius: 100%;
		font-size: 55upx;
		color: #FFFFFF;
	}

	.other-login .icon-weixin {
		background: #08D0AA;
	}

	.other-login .icon-xinlangweibo {
		background: #5499FF;
	}

	.other-login .icon-QQ {
		background: #FB9000;
	}
	
	.login-user-info>view:nth-child(1)>image {
		width: 90upx;
		height: 90upx;
		border-radius: 90upx;
		margin-right: 20upx;
	}
	
	.login-user-info-arrow {
		
	}

	.home-tabs {
		padding: 20upx;
	}

	.home-ad {
		padding: 20upx;
	}

	.home-ad>image {
		width: 100%;
		height: 150upx;
		border-radius: 20upx;
	}
</style>
