<template>
	<view>
		
		<view class="editLine pdlr4">
			<view class="item flexRowBetween">
				<view class="ll">姓名</view>
				<view class="rr flexEnd">
					<input type="text" value="" placeholder="请输入" placeholder-class="placeholder" />
				</view>
			</view>
			<view class="item flexRowBetween">
				<view class="ll">联系方式</view>
				<view class="rr flexEnd">
					<input type="text" value="" placeholder="请输入" placeholder-class="placeholder" />
				</view>
			</view>
		</view>
		
		<view class="submitbtn" style="margin-top: 300rpx;">
			<button class="btn" type="submit">确定</button>
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
	@import "../../assets/style/editInfor.css";
	page{padding-bottom: 30rpx;}
	.editLine .item .rr{font-size: 26rpx;}
	.editLine .item input{text-align: right;}
</style>
