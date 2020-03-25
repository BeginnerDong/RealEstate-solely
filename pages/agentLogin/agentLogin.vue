<template>
	<view>
		
		<view></view>
		<view class="loginCont fs13">
			<view class="fs20 ftw" style="padding-bottom: 80rpx;">账号登录</view>
			<view class="item flex mgb15">
				<view class="icon"><image src="../../static/images/the-loginl-icon.png" mode=""></image></view>
				<view class="input"><input type="text" placeholder="账号" placeholder-class="placeholder"></view>
			</view>
			<view class="item flex">
				<view class="icon"><image src="../../static/images/the-loginl-icon1.png" mode=""></image></view>
				<view class="input"><input type="password" placeholder="密码" placeholder-class="placeholder"></view>
			</view>
		</view>
		
		<view class="submitbtn" style="margin-top: 300rpx;">
			<button class="btn fs15" @click="Router.navigateTo({route:{path:'/pages/agentUser/agentUser'}})">登录</button>
		</view>
		<view class="loginBj">
			<image src="../../static/images/the-loginl-img.png" mode=""></image>
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


		},
	};
</script>

<style>
	.loginBj{width: 100%;height: 308rpx;position: fixed;left: 0;right: 0;bottom: 0;z-index: -1;}
	
	.loginCont{margin: 100rpx 10% 0 10%;}
	.loginCont .item{height: 80rpx;border-bottom: 1px solid #eee;}
	.loginCont .item .icon{width: 34rpx;height: 34rpx;margin-right: 20rpx;}
	.loginCont .item .icon image{width: 100%;height: 100%;}
	.loginCont .item .input{width: 87%;}
	.loginCont .item .input input{width: 100%;height: 60rpx;display: block;font-size: 28rpx;}
</style>
