<template>
	<view>
		
		<view class="banner-box pdlr4">
			<view class="banner pdt15">
				<swiper class="swiper-box" indicator-dots="true" autoplay="true" interval="3000" duration="1000" indicator-active-color="#ff5e43">
					<block v-for="(item,index) in labelData" :key="index">
						<swiper-item class="swiper-item">
							<image :src="item" class="slide-image" />
						</swiper-item>
					</block>
				</swiper>
			</view>
		</view>
		
		<view class="indHome flexRowBetween whiteBj mglr4 pdtb15 fs12">
			<view class="item"  @click="Router.navigateTo({route:{path:'/pages/projectAtlas/projectAtlas'}})">
				<image src="../../static/images/home-icon1.png"></image>
				<view class="tit">项目图集</view>
			</view>
			<view class="item" @click="Router.navigateTo({route:{path:'/pages/projectAdvantage/projectAdvantage'}})">
				<image src="../../static/images/home-icon2.png"></image>
				<view class="tit">项目优势</view>
			</view>
			<view class="item" @click="Router.navigateTo({route:{path:'/pages/matching/matching'}})">
				<image src="../../static/images/home-icon.png"></image>
				<view class="tit">相关配套</view>
			</view>
			<view class="item" @click="Router.navigateTo({route:{path:'/pages/onlineBooking/onlineBooking'}})">
				<image src="../../static/images/home-icon3.png"></image>
				<view class="tit">在线预约</view>
			</view>
		</view>
		
		<view class="f5H10"></view>
		
		<view class="mglr4 pdt15">
			<view class="fs16 ftw">西安恒大文化旅游局</view>
			<view class="fs13 color6 mgt5">西咸新区-秦汉新城</view>
			<view class="flex mgt5 tit-lable fs10">
				<view class="btn">度假</view>
				<view class="btn">投资</view>
				<view class="btn">品牌开发商</view>
			</view>
		</view>	
		<view class="">
			<view class="pdlr4 fs15 pdt5 ftw flex"><view class="titXian"></view>在售户型 (18)</view>
			<view class="sellHose fs13 pdl15 pdt15">
				<scroll-view scroll-x>
					<view class="item" v-for="(item,index) in proData" :key="index" @click="Router.navigateTo({route:{path:'/pages/hoseBanner/hoseBanner'}})">
						<view class="pic">
							<image src="../../static/images/home-img.png" mode=""></image>
						</view>
						<view class="infor">
							<view class="tit avoidOverflow">玺约瞰景高层</view>
							<view class="flex mgt5">
								<view class="ALPrice fs13 ftw red mgr10">112万</view>
								<view class="fs10 color9">97㎡</view>
							</view>
						</view>
					</view>
				</scroll-view>
				
			</view>
		</view>
		
		<view class="pdlr4">
			<view class="flexRowBetween msgTit center pdtb10">
				<view class="item">
					<view class="ftw tit">恒大</view>
					<view class="fs13 color6">开发商品牌</view>
				</view>
				<view class="item">
					<view class="ftw tit">洋房,高层,小高层</view>
					<view class="fs13 color6">建筑类别</view>
				</view>
				<view class="item">
					<view class="red tit">8800-10600</view>
					<view class="fs13 color6">价格</view>
				</view>
			</view>
			<view class="msgInfor fs12">
				<view class="item flexRowBetween">
					<view class="ll flex">
						<view class="tit">开盘时间</view>
						<view class="text">2020年4月20日 8:00</view>
					</view>
					<view class="rr flex">
						<view class="tit">交房时间</view>
						<view class="text">--</view>
					</view>
				</view>
				<view class="item flexRowBetween">
					<view class="ll flex">
						<view class="tit">产权年限</view>
						<view class="text avoidOverflow">住宅70年、公寓商户等等</view>
					</view>
					<view class="rr flex">
						<view class="tit">车位比</view>
						<view class="text">1:1:1</view>
					</view>
				</view>
				<view class="item">
					<view class="flex">
						<view class="tit">开发商</view>
						<view class="text">西安恒大世界旅游开发有限公司</view>
					</view>
				</view>
			</view>
			
			<view class="submitbtn mgt15 mgb20">
				<view class="btn flexCenter" style="display: flex;"  @click="Router.navigateTo({route:{path:'/pages/house-moreMsg/house-moreMsg'}})">查看更多<image class="arrowR" src="../../static/images/home-icon4.png" mode=""></image></view>
			</view>
		</view>
		
		
		<!--底部tab键-->
		<view class="navbar">
			<view class="navbar_item" @click="Router.redirectTo({route:{path:'/pages/index/index'}})">
				<view class="nav_img">
					<image src="../../static/images/nabar1-a.png" />
				</view>
				<view class="text this-text">首页</view>
			</view>
			<view class="navbar_item" @click="Router.redirectTo({route:{path:'/pages/interact/interact'}})" >
				<view class="nav_img">
					<image src="../../static/images/nabar2.png" />
				</view>
				<view class="text">互动</view>
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
				labelData: [
					"../../static/images/home-banner.png",
					"../../static/images/home-banner.png",
					"../../static/images/home-banner.png"
				],
				proData:[{},{},{},{},{},{}]
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
	
	.swiper-box {height: 300rpx;box-sizing: border-box;overflow: hidden;border-radius: 10rpx;}
	.swiper-box swiper-item{width: 100%;box-sizing: border-box;overflow: hidden;}
	.swiper-box swiper-item image {width: 100%;height: 100%;box-sizing: border-box;}
	
	/* 分类导航 */
	.indHome{ flex-wrap:wrap;}
	.indHome .item{width: 20%;text-align: center;color: #222;display: flex; flex-direction: column;}
	.indHome .item image{width:60rpx;height:60rpx; margin: 0 auto 10rpx auto; }
	
	.tit-lable .btn{height: 40rpx;line-height: 40rpx;padding: 0 12rpx;border: 1px solid #d8d8d8;color: #999;border-radius: 8rpx;margin: 0 20rpx 20rpx 0;}
	.titXian{width: 8rpx;height: 25rpx;background: #c39c57;margin-right: 10rpx;}
	
	.msgTit .tit{margin-bottom: 10rpx;}
	.msgInfor .item{margin-bottom: 20rpx;}
	.msgInfor .item .ll{width: 59%;}
	.msgInfor .item .rr{width: 40%;}
	.msgInfor .item .tit{color: #999;}
	.msgInfor .item .text{width: 57%;margin-left:16rpx;}
	.msgInfor .item .ll .text{width: 65%;}
	
	.sellHose .item{display: inline-block;width: 230rpx;height: 282rpx;margin: 0 20rpx 20rpx 0;box-sizing: border-box;}
	.sellHose .item .pic{width: 100%;height: 160rpx;box-sizing: border-box;border:1px solid #eee;}
	.sellHose .item .pic image{width: 100%;height: 100%;}
	.sellHose .item .infor{padding: 20rpx 0;line-height: 36rpx;}
	
	
	
	scroll-view{white-space: nowrap;}
	scroll-view .item{display: inline-block;}
</style>
