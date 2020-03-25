<template>
	<view>
		<view class="pdlr4 pdt15 pdb15 whiteBj">
			<view class="seachbox flex">
				<button class="seachBtn" type="button"><image src="../../static/images/the-customerl-icon.png" mode=""></image></button>
				<view class="input">
					<input type="text" name="" value="" placeholder="姓名、电话" placeholder-class="placeholder" />
				</view>
			</view>
		</view>
		<view class="mglr4">
			<view class="clientItem mgt15" v-for="(item,index) in clientData" :key="index">
				<view class="fs11 color9">日期：2020-03-25</view>
				<view class="flex mgt10 fs13">
					<view class="flex name">
						<view class="color6">姓名：</view>
						<view class="">张丹</view>
					</view>
					<view class="flex phoneNum">
						<view class="color6">电话：</view>
						<view class="">156235654879</view>
					</view>
				</view>
			</view>
		</view>
		
		<view class="R-fixIcon" @click="Router.navigateTo({route:{path:'/pages/agent-myClientAdd/agent-myClientAdd'}})">
			<image src="../../static/images/the-customerl-icon1.png" mode=""></image>
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
				clientData:[{},{},{}]
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
	page{padding-bottom:30rpx;background: #F5F5F5;}
	
	.seachbox{box-sizing: border-box;}
	.seachbox{background:#F5F5F5;height: 60rpx;border-radius: 10rpx;overflow: hidden;box-sizing: border-box;padding: 0 24rpx;}
	.seachbox .input{width:85%;}
	.seachbox .input input{width: 100%;line-height: 60rpx;padding: 0 20rpx 0 0px;box-sizing: border-box;display: block;border: none;font-size: 26rpx;}
	.seachbox .seachBtn{width: 36rpx;height: 36rpx; display: block;border: none;margin: 0;margin-right: 10rpx;}
	
	.clientItem{height: 160rpx;width: 100%;box-sizing: border-box;background: #fff;border-radius: 10rpx;padding: 30rpx 4%;}
	.clientItem .name{width: 40%;}
	.clientItem .phoneNum{width: 60%;}
	
	.R-fixIcon{width: 90rpx;height:90rpx;position: fixed;bottom:30%;right: 10rpx;z-index: 10;letter-spacing:4rpx;}
</style>
