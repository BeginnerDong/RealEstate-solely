<template>
	<view>
		
		<view class="advantage">
			<view class="item">
				<view class="flex tit">
					<view class="icon"><image src="../../static/images/advantagel-icon.png" mode=""></image></view>
					<view>交通配套</view>
				</view>
				<view class="text">项目位于西安市曲江大明宫板块，北接凤城五路、南邻凤城四路，紧邻地铁4号线(百花村站)、10号线 (在建)</view>
			</view>
			<view class="item">
				<view class="flex tit">
					<view class="icon"><image src="../../static/images/advantagel-icon1.png" mode=""></image></view>
					<view>教育资源</view>
				</view>
				<view class="text">项目自带中小学、市第十一中学、百花村小学、西航二校、西安高级中学</view>
			</view>
			<view class="item">
				<view class="flex tit">
					<view class="icon"><image src="../../static/images/advantagel-icon2.png" mode=""></image></view>
					<view>交通配套</view>
				</view>
				<view class="text">项目位于西安市曲江大明宫板块，北接凤城五路、南邻凤城四路，紧邻地铁4号线(百花村站)、10号线 (在建)</view>
			</view>
			<view class="item">
				<view class="flex tit">
					<view class="icon"><image src="../../static/images/advantagel-icon3.png" mode=""></image></view>
					<view>商场购物</view>
				</view>
				<view class="text">万达广场、四海唐人街、凤五赛高、水晶卡巴商业、凤七熙地港、大融城</view>
			</view>
			<view class="item">
				<view class="flex tit">
					<view class="icon"><image src="../../static/images/advantagel-icon4.png" mode=""></image></view>
					<view>生活娱乐</view>
				</view>
				<view class="text">大明宫遗址公园、城市运动公园、28亩城市绿地</view>
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
				is_show:false
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
	page{padding-bottom: 30rpx;}
	.advantage .item{padding: 30rpx 4%;border-bottom: 10rpx solid #F5F5F5;}
	.advantage .item .icon{width: 36rpx;height: 36rpx;margin-right: 20rpx;}
	.advantage .item image{width: 100%;height: 100%;}
	.advantage .item .tit{font-size: 30rpx; font-weight: bold;}
	.advantage .item .text{font-size: 26rpx; color: #464646;margin-top: 20rpx;}
</style>
