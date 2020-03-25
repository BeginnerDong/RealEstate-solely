<template>
	<view>
		
		
		<view class="mglr4 xqInfor pdt15">
			<view class="fs18 title">六大装修谣言现在还有人相信？真相在这里！</view>
			<view class="time fs12 color9 flex pdt10"><image class="timeIcon" src="../../static/images/interactivel-icon.png" mode=""></image>2020-03-24</view>
			<view class="cont fs13">
				<view><image class="w" src="../../static/images/detailsl-img.png" mode="widthFix"></image></view>
				<view>管理客服电话还房贷两个号和个梵蒂冈悲愤交加鹤骨鸡肤供货方点击可供货方都拉黑干活的放假开个会过分的话看刚发的刚发的个人个人赛退热贴热推监管科了付赛的价格过节费考虑到加工费来电管家发了个结果翻到鬼斧神工金融机构日就是个交管理费见到过和公司就发了活过来了供货方的记录可挂号费了家里就结果回访供货方健康的两个号</view>
				
				<view>发光时代个梵蒂冈就大概就过来发电机个梵蒂冈日ID高投入高京东方斯拉夫人GRE奥卡福乐山大佛开发票时家公司股票而可怕看鸟发动机是否会号放假肯定是付款说服力法人会健身房和热咖啡更好</view>
				
			</view>
		</view>
		
		
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				Router:this.$Router,
				is_show: false,
				wx_info:{},
				is_show:false
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
	@import "../../assets/style/detail.css";
	page{padding-bottom: 60rpx;line-height: 44rpx;}	
	
	.title{line-height: 50rpx;}
	.timeIcon{width: 26rpx;height: 26rpx;margin-right:8rpx;}
	
</style>
