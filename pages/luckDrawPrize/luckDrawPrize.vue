<template>
	<view>
		
		<view class="mglr4 center flexRowBetween cont pdt15">
			<view class="item" @click="changeCurr(index)" v-for="(item,index) in prizeData" :key="index">
				<view class="pic">
					<image src="../../static/images/interactivel-img5.png" mode=""></image>
				</view>
				<view class="tit">牙刷</view>
				<view class="">
					<image class="seltIcon"  :src="curr==index?'../../static/images/interactivel-icon2.png':'../../static/images/interactivel-icon1.png'"  mode=""></image>
				</view>
			</view>
		</view>
		
		<view class="submitbtn" style="margin-top:150rpx;">
			<button class="btn" type="submint">确定</button>
		</view>
		<view class="fs13 color9 mgt10 center pdlr4">每次只能选择一种礼品</view>
		
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
				is_show:false,
				curr:1,
				prizeData:[{},{},{},{},{},{}]
			}
		},
		onLoad() {
			const self = this;
			//self.$Utils.loadAll(['getMainData'], self);
		},
		methods: {
			changeCurr(index){
				const self = this;
				self.curr = index
			}
		}
	};
</script>

<style>
	page{}
	.pic{width: 200rpx;height: 200rpx;box-sizing: border-box;border: 1px solid #eee;}
	.seltIcon{width: 36rpx;height: 36rpx;margin: 0 auto;}
	.cont{flex-wrap: wrap;}
	.item{width: 200rpx;height: 310rpx;background-color: #fff;box-sizing: border-box;border-radius: 10rpx;margin-bottom: 40rpx;}
	.item .tit{font-size: 26rpx;margin: 20rpx 4%;}
</style>
