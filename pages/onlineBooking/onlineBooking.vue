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
				<view class="ll">电话</view>
				<view class="rr flexEnd">
					<input type="text" value="" placeholder="请输入" placeholder-class="placeholder" />
				</view>
			</view>
			<view class="item flexRowBetween">
				<view class="ll">验证码</view>
				<view class="rr flexEnd">
					<view style="width: 60%;">
						<input type="text" value="" placeholder="请输入" placeholder-class="placeholder" />
					</view>
					<view class="pubColor mgl10">获取验证码</view>
				</view>
			</view>
			<view class="item flexRowBetween">
				<view class="ll">选择日期</view>
				<view class="rr flexEnd">
					<view class="color9 mgl10">
						<picker mode="date" :value="date" :start="startDate" :end="endDate" @change="bindDateChange">
							<view class="uni-input">{{date}}</view>
						</picker>
					</view>
					
					<view>
						<image class="arrowR" src="../../static/images/about-icon11.png" mode=""></image>
					</view>
				</view>
			</view>
		</view>
		
		<view class="submitbtn" style="margin-top: 200rpx;">
			<button class="btn" type="submit">提交</button>
		</view>
</view>
</template>

<script>
	export default {
		data() {
			const currentDate = this.getDate({
					format: true
				})
			return {
				Router:this.$Router,
				is_show: false,
				wx_info:{},
				is_show:false,
				index: 0,
				date: currentDate,
			}
		},
		onLoad() {
			const self = this;
			// self.$Utils.loadAll(['getMainData'], self);
		},
		computed: {
			startDate() {
				return this.getDate('start');
			},
			endDate() {
				return this.getDate('end');
			}
		},
		methods: {
			 bindDateChange: function(e) {
				const self = this;
				self.date = e.target.value
			},
			getDate(type) {
				const date = new Date();
				let year = date.getFullYear();
				let month = date.getMonth() + 1;
				let day = date.getDate();
	
				if (type === 'start') {
					year = year - 60;
				} else if (type === 'end') {
					year = year + 2;
				}
				month = month > 9 ? month : '0' + month;;
				day = day > 9 ? day : '0' + day;
				return `${year}-${month}-${day}`;
			},
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
