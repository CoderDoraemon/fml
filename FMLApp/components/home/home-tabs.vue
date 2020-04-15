<template>
	<view class="home-tabs u-f-ajc">
		<block v-for="(item, index) in numbers" :key="index">
			<view class="u-f-column u-f1 u-f-ajc">
				{{ item.number }}<view class="">{{ item.title }}</view>
			</view>
		</block>
	</view>
</template>

<script>
	export default {
		props: {
			numbers: Array
		}
	}
</script>

<style scoped>
	
	.home-tabs {
		background-color: #FFFFFF;
		padding: 20upx;
	}
</style>
