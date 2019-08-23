<template>
	<view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		/* 导航栏按钮点击 */
		onNavigationBarButtonTap(e) {
			if (e.index == 0) {
				uni.navigateBack({
					delta: 1
				})
			}
		},
		methods: {
			
		}
	}
</script>

<style>

</style>
