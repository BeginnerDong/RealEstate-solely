<template>
	<view>
		
		<view class="mglr4 pdtb15 flexRowBetween">
			<view class="cards" @click="Router.navigateTo({route:{path:'/pages/luckDraw/luckDraw'}})">
				<image src="../../static/images/interactivel-img.png" mode=""></image>
			</view>
			<view class="cards" @click="Router.navigateTo({route:{path:'/pages/luckDrawPrize/luckDrawPrize'}})">
				<image src="../../static/images/interactivel-img1.png" mode=""></image>
			</view>
		</view>
		<view class="f5H5"></view>
		<view class="pdlr4">
			<view class="fs15 pdt15 ftw flex"><view class="titXian"></view>新闻动态</view>
			<view class="newsList">
				<view class="item flexRowBetween" v-for="(item,index) in newsData" :key="index" @click="Router.navigateTo({route:{path:'/pages/interactDetail/interactDetail'}})">
					<view class="infor">
						<view class="tit avoidOverflow2">六大装修谣言现在还有人相信？真相在这里！</view>
						<view class="time fs12 color9 flex"><image class="timeIcon" src="../../static/images/interactivel-icon.png" mode=""></image>2020-03-23</view>
					</view>
					<view class="pic">
						<image src="../../static/images/interactivel-img2.png" mode=""></image>
					</view>
				</view>
			</view>
		</view>
		
		
		<!--底部tab键-->
		<view class="navbar">
			<view class="navbar_item" @click="Router.redirectTo({route:{path:'/pages/index/index'}})">
				<view class="nav_img">
					<image src="../../static/images/nabar1.png" />
				</view>
				<view class="text">首页</view>
			</view>
			<view class="navbar_item" @click="Router.redirectTo({route:{path:'/pages/interact/interact'}})" >
				<view class="nav_img">
					<image src="../../static/images/nabar2-a.png" />
				</view>
				<view class="text this-text">互动</view>
			</view>
			<view class="navbar_item" @click="Router.redirectTo({route:{path:'/pages/user/user'}})" >
				<view class="nav_img">
					<image src="../../static/images/nabar3.png" />
				</view>
				<view class="text">我的</view>
			</view>
		</view>
		<!--底部tab键 end-->
		
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
				newsData:[{},{},{},{}]
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
	@import "../../assets/style/navbar.css";
	
	page{padding-bottom: 140rpx;}	
	.cards{width: 335rpx;height: 200rpx;border-radius: 10rpx;overflow: hidden;position: relative;}
	.titXian{width: 8rpx;height: 25rpx;background: #c39c57;margin-right: 10rpx;}
	
	.newsList .item{padding:30rpx 0;border-bottom: 1px solid #eee;align-items: flex-start; box-sizing: border-box;}
	.newsList .item .infor{width: 60%;height: 150rpx;position: relative;padding-bottom: 40rpx;box-sizing: border-box;}
	.newsList .item .infor .time{position: absolute;left:0;right: 0;bottom: 0;}
	.newsList .item .pic{width: 230rpx;height: 150rpx;}
	.timeIcon{width: 26rpx;height: 26rpx;margin-right:8rpx;}
</style>
