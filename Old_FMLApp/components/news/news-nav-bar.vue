<template>
	<view>
		<uni-nav-bar :fixed="true" :statusBar="true" :border="false" @click-right="openAdd">
			<!-- 中间 -->
			<view class="nav-tab-bar u-f-ajc">
				<block v-for="(tab,index) in tabBars" :key="tab.id">
					<view class="u-f-ajc  animated faster" 
					:class="{'font-lg main-color zoomIn':tabIndex==index}" 
					@tap="changeTab(index)">
						{{tab.name}}
					</view>
				</block>
			</view>
			<!-- 右边 -->
			<block slot="right">
				<view class="nav-right u-f-ajc">
					<view class="iconfont icon-fatie_icon"></view>
				</view>
			</block>
		</uni-nav-bar>
	</view>
</template>

<script>
	import uniNavBar from "../../components/uni-nav-bar/uni-nav-bar.vue";
	export default {
		components:{
			uniNavBar
		},
		props:{
			tabBars:Array,
			tabIndex:Number
		},
		methods:{
			changeTab(index){
				this.$emit('change-tab',index);
			},
			openAdd(){
				// 打开发布页面
				uni.navigateTo({
					url: '../add-input/add-input',
				});
			}
		}
	}
</script>

<style scoped>
.nav-left>view,.nav-right>view{
	font-size: 40upx;
}
.nav-left>view{
	color: #FF9619;
}
.nav-left{
	margin-left: 16upx;
}
.nav-right{
	width: 100%;
}
.nav-tab-bar{
	width: 100%;
	margin-left: -20upx;
	position: relative;
}
.nav-tab-bar>view{
	font-size: 32upx;
	padding: 0 15upx;
	font-weight: bold;
	color: #969696;
}
</style>
