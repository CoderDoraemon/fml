<template>
	<view class="u-f-ac">
		<view class="icon iconfont" :class="font">{{ number }}</view>
	</view>
</template>

<script>
	export default {
		props: {
			font: {
				type: String,
				default: ''
			},
			number: {
				type: Number,
				default: 0
			}
		},
		data() {
			return {
				
			}
		}
	}
</script>

<style>
</style>
