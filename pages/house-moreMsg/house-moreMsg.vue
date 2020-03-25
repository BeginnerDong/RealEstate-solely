<template>
	<view>
		<view class="">
			<view class="houseMsg">
				<view class="item">
					<view class="line flex">
						<view class="tit">楼盘详细地址</view>
						<view class="text">经纬大道与沣泾大道交汇处向西</view>
					</view>
					<view class="line flex">
						<view class="tit">合作开始时间</view>
						<view class="text">2020年03月24日</view>
					</view>
					<view class="line flex">
						<view class="tit">合作结束时间</view>
						<view class="text">2020年04月30日</view>
					</view>
				</view>
				<view class="item">
					<view class="line flex">
						<view class="tit">开盘时间</view>
						<view class="text">--</view>
					</view>
					<view class="line flex">
						<view class="tit">交房时间</view>
						<view class="text">--</view>
					</view>
					<view class="line flex">
						<view class="tit">产权年限</view>
						<view class="text">住宅70年、公寓商铺40年</view>
					</view>
					<view class="line flex">
						<view class="tit">物业公司</view>
						<view class="text">金币物业</view>
					</view>
				</view>
				<view class="item">
					<view class="line flex">
						<view class="tit">开发商</view>
						<view class="text">西安恒大童世界旅游开发有限公司</view>
					</view>
					<view class="line flex">
						<view class="tit">开发商品牌</view>
						<view class="text">恒大</view>
					</view>
				</view>
				<view class="item">
					<view class="line flex">
						<view class="tit">建筑面积</view>
						<view class="text">48万方</view>
					</view>
					<view class="line flex">
						<view class="tit">容积率</view>
						<view class="text">2.5</view>
					</view>
					<view class="line flex">
						<view class="tit">绿化率</view>
						<view class="text">56%</view>
					</view>
				</view>
				<view class="item">
					<view class="line flex">
						<view class="tit">总户数</view>
						<view class="text">5000</view>
					</view>
					<view class="line flex">
						<view class="tit">车位数</view>
						<view class="text">5500</view>
					</view>
					<view class="line flex">
						<view class="tit">车位比</view>
						<view class="text">1:1:1</view>
					</view>
				</view>
				<view class="item">
					<view class="line flex">
						<view class="tit">均价</view>
						<view class="text">8800-15235</view>
					</view>
					<view class="line flex">
						<view class="tit">得房率</view>
						<view class="text">--</view>
					</view>
					<view class="line flex">
						<view class="tit">物业费</view>
						<view class="text">--</view>
					</view>
					<view class="line flex">
						<view class="tit">物业类型</view>
						<view class="text">住宅，高层，小高层</view>
					</view>
					<view class="line flex">
						<view class="tit">装修状况</view>
						<view class="text">精装</view>
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
	page{padding-bottom: 30rpx;}
	.houseMsg .item{padding: 30rpx 4%;border-bottom: 20rpx solid #F5F5F5;}
	.houseMsg .item .line{margin-bottom: 20rpx;}
	.houseMsg .item .line:last-child{margin-bottom: 0;}
	.houseMsg .item .tit{width: 25%;color: #666;font-size: 26rpx;}
	.houseMsg .item .text{width:75%;box-sizing: border-box;padding-left: 10rpx;font-weight: bold;}
	
</style>
