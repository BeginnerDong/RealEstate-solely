<template>
	<view>
		
		<view class="orderNav flexRowBetween whiteBj">
			<view class="tt" :class="curr==1?'on':''" @click="currChange('1')">未到访</view>
			<view class="tt" :class="curr==2?'on':''" @click="currChange('2')">已到访</view>
		</view>
		<view class="mglr4 pdt15">
			<view class="reserve fs13" v-show="curr==1">
				<view class="item flexRowBetween" v-for="(item,index) in reserveData" :key="index">
					<view class="ll">
						<view class="line flex">
							<view class="tit">姓名：</view>
							<view class="text">张丹</view>
						</view>
						<view class="line flex">
							<view class="tit">电话：</view>
							<view class="text">15623565689</view>
						</view>
						<view class="line flex">
							<view class="tit">日期：</view>
							<view class="text">2019年3月25</view>
						</view>
					</view>
					<view class="rr center">
						<view class="fs12 mgb10 color9">核销码</view>
						<view class="code pubColor">12</view>
					</view>
				</view>
			</view>
			<view class="reserve fs13" v-show="curr==2">
				<view class="item flexRowBetween" v-for="(item,index) in reserveData" :key="index">
					<view class="hxIcon"><image src="../../static/images/yuyue-icon.png" mode=""></image></view>
					<view class="ll">
						<view class="line flex">
							<view class="tit">姓名：</view>
							<view class="text">李丽丽</view>
						</view>
						<view class="line flex">
							<view class="tit">电话：</view>
							<view class="text">18612345688</view>
						</view>
						<view class="line flex">
							<view class="tit">日期：</view>
							<view class="text">2019年3月25</view>
						</view>
					</view>
					<view class="rr center">
						<view class="fs12 mgb10 color9">核销码</view>
						<view class="code pubColor">86</view>
					</view>
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
				showView: false,
				score:'',
				wx_info:{},
				curr:1,
				reserveData:[{},{}]
			}
		},
		onLoad() {
			const self = this;
			//self.$Utils.loadAll(['getMainData'], self);
		},
		methods: {
			currChange(curr){
				const self = this;	
				if(curr!=self.curr){
					self.curr = curr
				}
			},
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
	@import "../../assets/style/orderNav.css";
	page{padding-bottom:30rpx;background: #F5F5F5;}
	.reserve .item{padding: 30rpx 4%;background: #fff;border-radius: 10rpx;position: relative;margin-bottom: 30rpx;}
	.reserve .item .ll{width: 70%;}
	.reserve .item .tit{color: #666;}
	.reserve .item .text{width: 75%;padding-left: 10rpx;box-sizing: border-box;}
	.reserve .item .line{margin-bottom:20rpx;}
	.reserve .item .line:last-child{margin-bottom: 0;}
	.reserve .item .rr{width: 30%;}
	.reserve .item .rr .code{font-size: 50rpx;line-height: 50rpx;font-weight: bold;}
	
	.hxIcon{width: 98rpx;height: 98rpx;position: absolute;top: 20rpx;right:20rpx;}
</style>
