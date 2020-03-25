<template>
	<view>
		
		<view class="userHead pr">
			<view class="headTit center white fs16">我的</view>
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
			<view class="item flexColumn" @click="Router.navigateTo({route:{path:'/pages/user-myReserve/user-myReserve'}})">
				<view class="icon"><image src="../../static/images/about-icon1.png" mode=""></image></view>
				<view>我的预约</view>
			</view>
			<view class="item flexColumn" @click="Router.navigateTo({route:{path:'/pages/user-myCode/user-myCode'}})">
				<view class="icon"><image src="../../static/images/about-icon2.png" mode=""></image></view>
				<view>我的推广码</view>
			</view>
			<view class="item flexColumn" @click="Router.navigateTo({route:{path:'/pages/user-myTeam/user-myTeam'}})">
				<view class="icon"><image src="../../static/images/about-icon3.png" mode=""></image></view>
				<view>我的团队</view>
			</view>
			<view class="item flexColumn" @click="Router.navigateTo({route:{path:'/pages/agentLogin/agentLogin'}})">
				<view class="icon"><image src="../../static/images/about-icon4.png" mode=""></image></view>
				<view>房产经纪人</view>
			</view>
			<view class="item flexColumn" @click="kefuShow">
				<view class="icon"><image src="../../static/images/about-icon5.png" mode=""></image></view>
				<view>联系客服</view>
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
					<image src="../../static/images/nabar2.png" />
				</view>
				<view class="text">互动</view>
			</view>
			<view class="navbar_item" @click="Router.redirectTo({route:{path:'/pages/user/user'}})" >
				<view class="nav_img">
					<image src="../../static/images/nabar3-a.png" />
				</view>
				<view class="text this-text">我的</view>
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
				showView: false,
				score:'',
				wx_info:{},
				is_kefuShow:false
			}
		},
		onLoad() {
			const self = this;
			//self.$Utils.loadAll(['getMainData'], self);
		},
		methods: {
			kefuShow(){
				const self = this;
				self.is_kefuShow = !self.is_kefuShow 
			},
			tel(){
				const self = this;
				uni.makePhoneCall({
					phoneNumber: '15623568989',
				})
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
	@import "../../assets/style/navbar.css";
	page{padding-bottom: 130rpx;}
	.uni-page-head{border-bottom: 0;}
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
