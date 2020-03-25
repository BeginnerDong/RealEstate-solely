<template>
	<view>
		<view class="pdlr4">
			<view class="atlas pdtb10">
				<view class="item" v-for="(item,index) in atlasData" :key="index">
					<image :src="item" mode="widthFix"></image>
				</view>
			</view>
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				Router:this.$Router,
				is_show: false,
				wx_info:{},
				is_show:false,
				atlasData:[
					'../../static/images/atlasl-img.png',
					'../../static/images/atlasl-img1.png',
					'../../static/images/atlasl-img2.png',
					'../../static/images/atlasl-img3.png',
					'../../static/images/atlasl-img1.png',
					'../../static/images/atlasl-img3.png',
					'../../static/images/atlasl-img.png',
					'../../static/images/atlasl-img1.png',
					'../../static/images/atlasl-img2.png'
				]
			}
		},
		onLoad() {
			const self = this;
			// self.$Utils.loadAll(['getMainData'], self);
		},
		methods: {
			getMainData() {
				const self = this;
				console.log('852369')
				const postData = {};
				postData.tokenFuncName = 'getProjectToken';
				self.$apis.orderGet(postData, callback);
			}
		}
	};
</script>

<style>
	
	page{padding-bottom: 30rpx;background: #F5F5F5;}	
	.atlas{column-count: 5;column-width: 335rpx;column-gap: 20rpx;}
	.atlas .item{margin-bottom: 20rpx;border-radius: 10rpx;overflow: hidden;break-inside: avoid;}
	.atlas .item image{width: 100%;height: 100%;}
</style>
