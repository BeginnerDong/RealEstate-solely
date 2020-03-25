<template>
	<view>
		
		<view class="myMoney pdlr4 center pr">
			<view class="txBtn" @click="Router.navigateTo({route:{path:'/pages/user-cashOut/user-cashOut'}})">提现</view>
			<view class="flexCenter">
				<image style="width: 140rpx;height: 140rpx;" src="../../static/images/commissionl-icon.png" mode=""></image>
			</view>
			<view class="fs13 mgt10 mgb10">金额 (￥)</view>
			<view class="bigNum ftw">200</view>
		</view>
		
		<view class="f5H10"></view>
		
		<view class="myRowBetween fs13 mglr4 ">
			<view class="item flexRowBetween" v-for="(item,index) in tuiguangData" :key="index">
				<view class="ll">
					<view class="">提现</view>
					<view class="fs13 color9">2020-3-25</view>
				</view>
				<view class="rr red">-56</view>
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
				tuiguangData:[{},{},{},{}],
				browseData:[{},{},{},{}]
			}
		},
		onLoad() {
			const self = this;
			//self.$Utils.loadAll(['getMainData'], self);
		},
		methods: {

		},
	};
</script>

<style>
	@import "../../assets/style/orderNav.css";
	@import "../../assets/style/editInfor.css";
	
	page{padding-bottom: 130rpx;}
	.myMoney{height: 360rpx;box-sizing: border-box;padding-top: 40rpx;}
	.myMoney .bigNum{font-size: 54rpx;line-height: 54rpx;}
	
	.txBtn{width: 120rpx;height: 56rpx;line-height: 56rpx;text-align: center;border-radius: 36rpx;color: #fff;background-color: #C39C57;position: absolute; top: 30rpx;right: 4%;}
	.myRowBetween .item .rr{font-size: 28rpx;}
	
</style>
