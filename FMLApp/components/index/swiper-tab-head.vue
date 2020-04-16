<template>
	<view>
		
		<block v-if="layoutType===0">
			<scroll-view scroll-x class="bg-white nav" scroll-with-animation :scroll-left="scrollLeft">
				<view class="cu-item" :class="{'text-yellow': index==TabCur, 'cur': index==TabCur&showBottomLine} " v-for="(item,index) in tabBars" :key="index" @tap="tabSelect" :data-id="index">
					{{item.name}}
				</view>
			</scroll-view>
		</block>
		
		<block v-else-if="layoutType===1">
			<scroll-view scroll-x class="bg-white nav text-center">
				<view class="cu-item" :class="{'text-yellow': index==TabCur, 'cur': index==TabCur&showBottomLine} " v-for="(item,index) in tabBars" :key="index" @tap="tabSelect" :data-id="index">
					{{item.name}}
				</view>
			</scroll-view>
		</block>
		
		<block v-else>
			
			<scroll-view scroll-x class="bg-white nav">
				<view class="flex text-center">
					<view class="cu-item flex-sub" :class="{'text-yellow': index==TabCur, 'cur': index==TabCur&showBottomLine} " v-for="(item,index) in tabBars" :key="index" @tap="tabSelect" :data-id="index">
						{{item.name}}
					</view>
				</view>
			</scroll-view>
			
		</block>
		
	</view>
	
	
</template>

<script>
	/**
	 * 顶部滚动
	 * @description 顶部滚动
	 * @tutorial 
	 * @property {Number} layoutType = 【0|1|2】【居右|居中|平分】
	 * @property {Boolean} showBottomLine = 【0|1】【不显示|显示】
	 * @property {Array} tabBars = 数据源
	 * @event {Function} click 点击 fav按钮触发事件
	 */
	export default {
		props:{
			layoutType: {
				type: Number,
				default: 0
			},
			showBottomLine: {
				type: Boolean,
				default: 1
			},
			TabCur: {
				type: Number,
				default: 0
			},
			tabBars: Array
		},
		data() {
			return {
				scrollLeft: 0
			};
		},
		methods:{
			tabSelect(e) {
				this.TabCur = e.currentTarget.dataset.id;
				this.scrollLeft = (e.currentTarget.dataset.id - 1) * 60
				this.$emit('tabSelect',this.TabCur);
			}
		}
	}
</script>

<style>

</style>
