<template>
	<view class="px-3">
		<view class="uni-uploader">
			<view class="uni-uploader-head" v-if="imageList.length > 0">
				<view class="uni-uploader-title main-light-dark">点击可预览选好的图片</view>
				<view class="uni-uploader-info">{{imageList.length}}/9</view>
			</view>
			<view class="uni-uploader-body">
				<view class="uni-uploader__files">
					<block v-for="(image,index) in imageList" :key="index">
						<view class="uni-uploader__file rounded">
							<view class="iconfont icon-shanchu flex align-center justify-center rounded" @tap="delect(index)" style="width: 50rpx;height: 50rpx;"></view>
							<image class="uni-uploader__img rounded" :src="image" :data-src="image" @tap="previewImage" mode="aspectFill"></image>
						</view>
					</block>
					<view class="uni-uploader__input-box rounded" 
					v-if="imageList.length > 0">
						<view class="uni-uploader__input" @tap="chooseImage"></view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	var sourceType = [
		['camera'],
		['album'],
		['camera', 'album']
	]
	var sizeType = [
		['compressed'],
		['original'],
		['compressed', 'original']
	]
	export default {
		props: {
			imageList: Array,
		},
		data() {
			return {
				sourceTypeIndex: 2,
				sourceType: ['拍照', '相册', '拍照或相册'],
				sizeTypeIndex: 0,
				sizeType: ['压缩', '原图', '压缩或原图'],
				countIndex: 8,
				count: [1, 2, 3, 4, 5, 6, 7, 8, 9]
			}
		},
		created() {},
		methods:{
			chooseImage: async function() {
				if (this.imageList.length === 9) { return; }
				uni.chooseImage({
					sourceType: sourceType[this.sourceTypeIndex],
					sizeType: sizeType[this.sizeTypeIndex],
					count: this.imageList.length + this.count[this.countIndex] > 9 ? 9 - this.imageList.length : this.count[this.countIndex],
					success: (res) => {
						for (let i = 0; i < res.tempFilePaths.length; i++) {
							this.Upload(res.tempFilePaths[i]);
						}
					}
				})
			},
			// 上传多图
			async Upload(filePath){
				try{
					let [err2,res2] = await this.$http.upload('/image/uploadmore',{
						name: 'imglist[]',
						filePath:filePath,
						token:true,
						checkToken:true
					});
					let data = JSON.parse(res2.data);
					// 上传失败
					if (err2 || data.errorCode) {
						uni.showToast({ title: data.msg ? data.msg : '上传失败', icon:"none" });
						return false;
					}
					// 上传成功
					let list = data.data.list;
					// 通知父组件
					this.$emit('upload',list[0])
				}catch(e){
					return;
				}
			},
			previewImage: function(e) {
				var current = e.target.dataset.src
				uni.previewImage({
					current: current,
					urls: this.imageList
				})
			},
			delect(index){
				uni.showModal({
					title: '提示',
					content: '是否要删除该图片',
					success: (res)=> {
						if (res.confirm) {
							this.$emit('del',index)
						}
					}
				});
			}
		}
	}
</script>

<style>
	.cell-pd {
		padding: 22upx 30upx;
	}
	.uni-uploader__file{
		position: relative;
	}
	.list-pd {
		margin-top: 50upx;
	}
	.icon-shanchu{
		position: absolute;
		right: 0;
		top: 0;
		background: rgba(0,0,0,0.4);
		color: #FFFFFF;
		z-index: 100;
	}
</style>
