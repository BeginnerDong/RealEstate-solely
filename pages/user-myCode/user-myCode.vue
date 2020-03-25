<template>
	<view>
		
		<view class="codeCont pr white">
			<view class="bj"><image src="../../static/images/promotion-codel-img.png" mode=""></image></view>
			<view class="title center ftw pdtb25">房地产推广二维码</view>
			<view class="ewm"><image src="../../static/images/promotion-codel-img1.png" mode=""></image></view>
			<view class="flexCenter userName" style="padding-top: 70rpx;">
				<view class="photo"><image src="../../static/images/about-img1.png" mode=""></image></view>
				<view class="fs15 mgl10">快乐的猫</view>
			</view>
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				Router:this.$Router,
				showView: false,
				score:'',
				wx_info:{}
			}
		},
		onLoad() {
			const self = this;
			//self.$Utils.loadAll(['getMainData'], self);
		},
		methods: {
			getMainData() {
				const self = this;
				console.log('852369')
				const postData = {};
				postData.tokenFuncName = 'getProjectToken';
				self.$apis.orderGet(postData, callback);
			}

		},
	};
</script>

<style>
	
	.codeCont{width: 667rpx;height: 938rpx;margin: 100rpx auto;box-sizing: border-box;padding: 0 4%;}
	.codeCont .bj{position: absolute;top: 0;right: 0;bottom: 0;left: 0;z-index: -1;}
	.title{font-size: 48rpx;line-height: 66rpx;letter-spacing: 6rpx;}
	.ewm{width:370rpx;height: 370rpx;margin: 60rpx auto;border-right: 1px solid #ccc;border-bottom: 1px solid #ccc;box-sizing: border-box;}
	.photo{width: 60rpx;height: 60rpx;border-radius: 50%;overflow: hidden;}
</style>
