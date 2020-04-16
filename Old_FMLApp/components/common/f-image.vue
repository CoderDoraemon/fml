<template>
	<view>
		<view v-if="!show" :style="imageStyle" class="loading" :class="imageClass">
			{{msg}}
		</view>
		<image v-show="show" :src="imgSrc" @error="error"
		 @load="load" :mode="mode" lazy-load
		:style="imageStyle" :class="imageClass"
		@click="$emit('click')"></image>
	</view>
</template>

<script>
	export default {
		props: {
			imageClass:{
				type: String,
				default:'rounded'
			},
			src: {
				type: String,
				default: ""
			},
			text:{
				type: String,
				default: "加载中..."
			},
			imageStyle:{
				type: String,
				default: "width:710rpx;height:350rpx;"
			},
			mode:{
				type:String,
				default:""
			},
			errorText:{
				type:String,
				default:"图片加载失败"
			}
		},
		data() {
			return {
				msg:this.text,
				show:false
			}
		},
		computed: {
			imgSrc() {
				return this.src ? this.src : '/static/default.jpg' 
			}
		},
		methods: {
			error(){
				this.msg = this.errorText
			},
			load(e){
				this.show = true
			}
		},
	}
</script>

<style scoped>
	.loading{
		display: flex;
		align-items: center;
		justify-content: center;
		color: #BBBBBB;
		font-size: 30rpx;
		background-color: #F4F4F4;
	}
</style>
