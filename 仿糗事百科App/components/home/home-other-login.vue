<template>
	
	<view>
		<!-- <home-other-login></home-other-login> -->
		<view class="u-f-ajc other-login-tip">登陆仿糗事百科，体验更多功能</view>
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
	</view>
	
</template>

<script>
</script>

<style scoped>
	
	.other-login-tip {
		margin-top: 30upx;
	}
	
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
	
</style>
