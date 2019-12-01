<template>
	<view>
		<!-- 未登录 -->
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
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			
		}
	}
</script>

<style>

.other-login {
	padding: 40upx 80upx;
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
