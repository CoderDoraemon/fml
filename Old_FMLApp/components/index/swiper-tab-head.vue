<template>
	<view class="uni-tab-bar">
		<scroll-view scroll-x class="uni-swiper-tab border-0" :style="scrollStyle">
			<block v-for="(tab,index) in tabBars" :key="tab.id">
				<view class="swiper-tab-list animated faster" 
				:class="tabIndex===index ? 'font-lg main-color zoomIn' : 'pulse'"
				@tap="tabtap(index)"
				:style="scrollItemStyle">
					{{tab.name}} {{tab.num?tab.num:''}}
				</view>
			</block>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		props:{
			tabBars:Array,
			tabIndex:Number,
			scrollStyle:{
				type:String,
				default:""
			},
			scrollItemStyle:{
				type:String,
				default:""
			}
		},
		methods:{
			tabtap(index){
				this.$emit('tabtap',index);
			},
		}
	}
</script>

<style>
.uni-swiper-tab{
	border-bottom: 1upx solid #EEEEEE;
}
.swiper-tab-list{
	color: #333333;
	font-weight: bold;
}
</style>
