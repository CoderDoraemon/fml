<template>
	<view class="paper-list u-f-ac" @tap="itemClick(index)">
		<image class="u-f-sh" :src="item.userpic" mode="widthFix"></image>
		<view class="u-f-column u-f1">
			<view class="u-f-ac u-f-jsb u-line-one">
				{{ item.username }}
				<view>{{ item.time }}</view>
			</view>
			<view class="u-f-ac u-f-jsb">
				{{ item.data }}
				<template v-if="item.noreadnum > 0">
					<uni-badge :text="item.noreadnum" type="error"></uni-badge>
				</template>
				
			</view>
		</view>
	</view>
</template>

<script>
	import uniBadge from "../../components/uni-badge/uni-badge.vue";
	
	export default {
		components: {
			uniBadge,
		},
		props: {
			item: Object,
			index: Number
		},
		methods: {
			itemClick(index) {
				this.$emit("itemClick", index);
			}
		}
	}
</script>

<style scoped>
	.paper-list {
		border-bottom: 1upx solid #e5e5e5;
		padding: 30upx 30upx;
		width: calc(100% - 60upx);
	}

	.paper-list>image {
		width: 100upx;
		height: 100upx;
		border-radius: 100upx;
		margin-right: 30upx;
	}

	.paper-list>view {}

	.paper-list>view>view>view:last-child {
		width: 120upx;
		text-align: right;
	}
</style>
