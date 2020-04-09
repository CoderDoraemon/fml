<template>
	<view>

		<!-- 自定义导航栏 -->
		<uni-nav-bar :statusBar="true" rightText="发布" left-icon="back" @click-left="back" @click-right="submit">
			<view class="u-f-ajc titleFont" @tap="changelook">
				{{ title }}
				<view class="icon iconfont icon-xialazhankai"></view>
			</view>
		</uni-nav-bar>

		<!-- 多行输入框 -->
		<view class="uni-textarea">
			<textarea v-model="text" placeholder="说一句话吧~" />
			</view>
		
		<!-- 图片选择 -->
		<upload-images @upload="upload"></upload-images>
		
		<!-- 弹窗 -->
		<uni-popup ref="popup" type="center" mask-click="true">
			<view class="gonggao">
				<view class="u-f-ajc">
					<image src="../../static/common/addinput.png" mode="widthFix"></image>
				</view>
				<view class="gonggao-text">111111111111111</view>
				<view class="gonggao-text">222222222222222</view>
				<view class="gonggao-text">333333333333333</view>
				<view class="gonggao-text">444444444444444</view>
				<button type="default" @click="change">朕知道了</button>
			</view>
		</uni-popup>
		
	</view>
</template>

<script>
	
	import uniNavBar from '../../components/uni-nav-bar/uni-nav-bar.vue';
	import uploadImages from '../../components/common/upload-images.vue';
	import uniPopup from '../../components/uni-popup/uni-popup.vue';
	
	export default {
		components: {
			uniNavBar,
			uploadImages,
			uniPopup,
		},
		data() {
			return {
				isget: false,
				showpopup: true,
				title: "所有人可见",
				titles: ['所有人可见', '仅自己可见'],
				text: "",
				imageList: []
			}
		},
		onLoad() {
			this.$refs.popup.open();
		},
		onBackPress() {
			
			if (!this.text.length && this.imageList.length<1) { return }
			
			if (!this.isget) {
				this.caogao();
				return true;
			}
		},
		methods: {
			caogao() {
				uni.showModal({
					title: '提示',
					content: '是否要保存',
					cancelText: '不保存',
					confirmText: '保存',
					success: res => {
						if (res.confirm) {
							
						}
						
						this.isget = true
						uni.navigateBack({
							delta: 1,
						});
					}
				});
			},
			changelook() {
				uni.showActionSheet({
				    itemList: this.titles,
				    success: (res)=> {
						this.title = this.titles[res.tapIndex]
				    }
				});
			},
			back() {
				uni.navigateBack({
					delta: 1
				});
			},
			upload(res) {
				console.log(res);
			},
			change() {
				this.$refs.popup.close();
			}
		}
	}
		
		
		
</script>

<style>
	
	.titleFont {
		font-size: 36upx;
	}
	
	.uni-textarea {
		border: 1upx solid #EEEEEE;
	}
	
	.gonggao {
		background: #FFFFFF;
		width: 500upx;
		padding: 30upx;
	}
	
	.gonggao image {
		width: 65%;
		margin-bottom: 30upx;
	}
	
	.gonggao .gonggao-text {
		color: #333333;
		margin-bottom: 15upx;
	}
	
	.gonggao button {
		background: #F4FF11;
		color: #333333;
	}
	
</style>
