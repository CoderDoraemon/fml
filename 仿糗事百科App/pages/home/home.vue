<template>
	<view class="home-page">
		
		<!-- 未登录 -->
		<template v-if="isLogin">
			<homeLogin :userInfo="userInfo"></homeLogin>
		</template>
		
		<template v-else>
			<home-other-login></home-other-login> 
		</template>
		
		<!-- 横向bar -->
		<homeTabs :numbers="numbers"></homeTabs>
		
		<!-- 广告位 -->
		<view class="home-ad u-f-ajc">
			<image src="../../static/demo/banner3.jpg" mode="widthFix" lazy-load></image>
		</view>
		
		<!-- 列表 -->
		<block v-for="(item, index) in list" :key="index">
			<home-list-item :item="item"></home-list-item>
		</block>
		
		
	</view>
</template>

<script>
	
	import homeListItem from '../../components/home/home-list-item.vue';
	import homeOtherLogin from '../../components/home/home-other-login.vue';
	import homeLogin from '../../components/home/home-login.vue';
	import homeTabs from '../../components/home/home-tabs.vue';
	
	export default {
		components: {
			homeOtherLogin,
			homeListItem,
			homeLogin,
			homeTabs,
		},
		data() {
			return {
				isLogin: true,
				userInfo: {
					avatar: "../../static/demo/userpic/1.jpg",
					name: "昵称",
					total_number: 100,
					today_number: 1
				},
				numbers: [
					{
						title: "帖子",
						number: 37
					},
					{
						title: "动态",
						number: 46
					},
					{
						title: "评论",
						number: 12
					},
					{
						title: "粉丝",
						number: 10
					}
				],
				list: [
					{
						title: "浏览历史",
						icon: "liulan"
					},
					{
						title: "社区认证",
						icon: "huiyuanvip"
					},
					{
						title: "审核帖子",
						icon: "keyboard"
					}
				]
			}
		},
		methods: {
			
		},
		onNavigationBarButtonTap: (res) => {
			console.log(res.index)
			switch (res.index){
				case 0:
				uni.navigateTo({
					url: '../setter/setter'
				})
					break;
				default:
					break;
			}
		}
	}
</script>

<style>
	
	.home-ad {
		padding: 20upx;
	}

	.home-ad>image {
		width: 100%;
		height: 150upx;
		border-radius: 20upx;
	}
	
</style>
