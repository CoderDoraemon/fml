<template>
	<view>
		<!-- 列表 -->
		<block v-for="(item, index) in list" :key="index">
			<home-list-item :item="item"></home-list-item>
		</block>
		
		<button class="login-out" type="primary">退出登录</button>
		
	</view>
</template>

<script>
	import homeListItem from '../../components/home/home-list-item.vue';
	export default {
		components: {
			homeListItem
		},
		data() {
			return {
				list: [
					{
						title: "账户与安全"
					},
					{
						title: "资料编辑"
					},
					{
						title: "清除缓存"
					},
					{
						title: "意见反馈"
					},
					{
						title: "关于社区"
					}
				]
			}
		},
		methods: {
			
		}
	}
</script>

<style>
	
	.login-out {
		background: #E9657E!important;
		color: #FFFFFF;
		height: 88upx;
		margin: 30upx;
		border-radius: 88upx;
		font-weight: bold;
	}

</style>
