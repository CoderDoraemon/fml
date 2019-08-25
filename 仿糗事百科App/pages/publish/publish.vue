<template>
	<view>
		
		<!-- 自定义导航栏 -->
		<uni-nav-bar :statusBar="true" rightText="发布" left-icon="back" @click-left="back" @click-right="submit">
			<view class="u-f-ajc" @tap="changelook">
				{{getType}}
				<view class="icon iconfont icon-xialazhankai"></view>
			</view>
		</uni-nav-bar>
		
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
				getType: "所有人可见",
				itemList: ['A', 'B', 'C'],
			}
		},
		methods: {
			changelook() {
				uni.showActionSheet({
				    itemList: this.itemList,
				    success: (res)=> {
				        console.log('选中了第' + (res.tapIndex + 1) + '个按钮');
						this.getType = this.itemList[res.tapIndex]
				    },
				    fail: function (res) {
				        console.log(res.errMsg);
				    }
				});
			},
			back() {
				uni.navigateBack({
					delta: 1
				})
			}
		}
	}
</script>

<style>

</style>
