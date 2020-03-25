<template>
	<view>
		
		<view class="userHead pr">
			<view class="headTit center white fs16 pr">
				<view class="backBtn" @click="back()"><image src="../../static/images/back-icon.png" mode=""></image></view>房产经纪人</view>
			<view class="headbj"><image src="../../static/images/about-img.png" mode=""></image></view>
			<view class="infor radius10 boxShaow whiteBj">
				<view class="flexCenter">
					<image class="photo" src="../../static/images/about-img1.png" mode=""></image>
				</view>
				<view class="fs15 mgt10 center">加快速度</view>
			</view>
		</view>
		
		
		<view class="twoBox flexRowBetween mgt25 fs14 color6">
			<view class="item flexColumn" @click="Router.navigateTo({route:{path:'/pages/user-myMoney/user-myMoney'}})">
				<view class="icon"><image src="../../static/images/about-icon.png" mode=""></image></view>
				<view>我的佣金</view>
			</view>
			<view class="item flexColumn" @click="Router.navigateTo({route:{path:'/pages/agent-myReserve/agent-myReserve'}})">
				<view class="icon"><image src="../../static/images/about-icon1.png" mode=""></image></view>
				<view>预约管理</view>
			</view>
			<view class="item flexColumn" @click="Router.navigateTo({route:{path:'/pages/agent-myClient/agent-myClient'}})">
				<view class="icon"><image src="../../static/images/about-icon3.png" mode=""></image></view>
				<view>客户管理</view>
			</view>
			<view class="item flexColumn" @click="Router.navigateTo({route:{path:'/pages/user-myCode/user-myCode'}})">
				<view class="icon"><image src="../../static/images/about-icon2.png" mode=""></image></view>
				<view>我的推广码</view>
			</view>
			
		</view>
		
		<!-- 客服弹框 -->
		<view class="kefuNum flexCenter fs15 white" v-show="is_kefuShow">
			<view class="closeBtn" @click="kefuShow">×</view>
			<view class="flexCenter" @click="tel">
				<view style="width: 34rpx;height: 34rpx;"><image src="../../static/images/kefu-icon.png" mode=""></image></view>
				<view class="mgl5">15623568989</view>
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
			back(){
				const self = this;
				self.$router.go(-1)
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
	@import "../../assets/style/editInfor.css";
	page{padding-bottom: 130rpx;}
	.backBtn{width:20rpx;height: 35rpx;position: absolute;top: 50%;left: 30rpx;transform: translateY(-50%);}
	
	
	.headTit{height: 88rpx;line-height: 88rpx;background: #222;}
	
	.headbj{width: 100%;height: 349rpx;position: absolute;top: 0;right: 0;bottom: 0;left: 0; z-index: -1;}
	.headbj image{width: 100%;height: 100%;}
	.userHead .infor{width: 80%;height: 255rpx;margin: 0 auto;padding: 30rpx 4%;box-sizing: border-box;position:relative ;margin-top: 80rpx;}
	
	.userHead .photo{width: 120rpx;height: 120rpx;border-radius: 50%;margin-right: 20rpx;box-sizing: border-box;}
	
	.twoBox{flex-wrap:wrap ;}
	.twoBox .item{width: 33.33%;padding: 30rpx 0;}
	.twoBox .item .icon{width: 60rpx;height: 60rpx;display: block;margin: 0 auto 20rpx auto;}
	.twoBox .item .icon image{width: 100%;height: 100%;}
	
	.kefuNum{height: 140rpx;padding: 0 60rpx;position: fixed;top: 50%;left: 50%;transform: translate(-50%);background: rgba(0,0,0,0.5);}
	.kefuNum .closeBtn{bottom: auto;left: auto;right: -50rpx;top: -30rpx;}
</style>
