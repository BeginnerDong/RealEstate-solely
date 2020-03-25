<template>
	<view>
		
		<view class="mglr4 pdt15">
			<view class="reserve fs13">
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
					<view class="rr flexCenter">
						<view class="hxBtn fs13">确认核销</view>
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
				reserveData:[{},{}]
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
	@import "../../assets/style/orderNav.css";
	page{padding-bottom:30rpx;background: #F5F5F5;}
	.reserve .item{padding: 30rpx 4%;background: #fff;border-radius: 10rpx;position: relative;margin-bottom: 30rpx;}
	.reserve .item .ll{width: 70%;}
	.reserve .item .tit{color: #666;}
	.reserve .item .text{width: 75%;padding-left: 10rpx;box-sizing: border-box;}
	.reserve .item .line{margin-bottom:20rpx;}
	.reserve .item .line:last-child{margin-bottom: 0;}
	.reserve .item .rr{width: 30%;}
	
	.hxBtn{width: 150rpx;height: 56rpx;line-height: 56rpx;border-radius: 10rpx;border: 1px solid #C39C57; color: #C39C57;text-align: center;}
</style>
