<template>  
    <view> 
		<view class="main pdt20"> 
			<view class="canvas-container">  
				<view :animation="animationData" class="canvas-content" >  
					<view class="canvas-list">  
						<view class="canvas-item" v-for="(iteml,index2) in awardsList" :key="index2">  
							<view class="canvas-item-text" :style="[{transform:'rotate('+iteml.turn+')'}]">  
								<text>{{iteml.award}}</text>
							</view>  
						</view>  
					</view>  
				</view>  
				<view class="canvas-btn" v-bind:class="btnDisabled">
					<image src="../../static/images/interactivel-img4.png" mode=""></image>
				</view>
				
			</view>  
		</view> 
		
		<view class="submitbtn" style="margin-top: 100rpx;">
			<view class="btn" @tap="playReward">抽奖</view>
		</view>
    </view>  
</template>
<script>  
    export default {  
		data() {  
			return {  
				Router:this.$Router,
				showView: false,
				awardsConfig:{  
					chance: true,  
					awards: [  
						{ index: 0, name: '牙刷',type:0},
						{ index: 1, name: '毛巾',type:1},
						{ index: 2, name: '肥皂',type:0},
						{ index: 3, name: '杯子',type:1},
						{ index: 4, name: '梳子',type:0},
						{ index: 5, name: '无',type:1},
						{ index: 6, name: '脸盆',type:1},
						{ index: 7, name: '洗衣液',type:1},
						{ index: 8, name: '筷子',type:1},
						{ index: 9, name: '牙膏',type:1}
					]  
				},  
				awardsList: {},  
				animationData: {},  
				btnDisabled: '',  
				chishu:2 //点击次数 
			};  
		},  
		onLoad:function(){  
			
		},  
		onReady: function (e) {  
				this.drawAwardRoundel();  

				//分享  
				uni.showShareMenu({  
					withShareTicket: true  
				});  
		},  
		methods: {  

			//画抽奖圆盘  
			drawAwardRoundel: function () {			   
					var awards = this.awardsConfig.awards;  
					var awardsList = [];  
					var turnNum = 1 / awards.length*360;  // 文字旋转 turn 值  

					// 奖项列表  
					for (var i = 0; i < awards.length; i++) {  
					  awardsList.push({ turn: i * turnNum + 'deg', lineTurn: i * turnNum + turnNum / 2 + 'deg', award: awards[i].name });  
					}  

					this.btnDisabled = this.awardsConfig.chance ? '' : 'disabled';  
					this.awardsList = awardsList;  
			},

			//发起抽奖  
			playReward: function () { 
				if (this.chishu == 0) {  
					uni.showToast({  
						title:'抽奖次数已经用完',  
						icon:'none'  
					})  
					return  
				}  
				//中奖index
				var awardsNum = this.awardsConfig.awards;  
				var awardIndex = Math.round(Math.random()*(awardsNum.length-1));//随机数  
				var runNum = 10;//旋转10周  
				var duration = 3000;//时长  

				// 旋转角度  
				this.runDeg = this.runDeg || 0;  
				this.runDeg = this.runDeg + (360 - this.runDeg% 360) + (360 * runNum - awardIndex * (360 / awardsNum.length))
				//创建动画  
				var animationRun = uni.createAnimation({  
				  duration: duration,  
				  timingFunction: 'ease'  
				})  
				animationRun.rotate(this.runDeg).step();  
				this.animationData= animationRun.export();  
				this.btnDisabled= 'disabled';  

				//中奖提示  
				var awardsConfig = this.awardsConfig;  
				var awardType = awardsConfig.awards[awardIndex].type;     
				this.chishu = this.chishu - 1;  
				if (awardType == 0) {  
					setTimeout(function () {  
						uni.showModal({  
							title: '恭喜',  
							content: '获得' + (awardsConfig.awards[awardIndex].name),  
							showCancel: false  
						});  
						this.btnDisabled= '';
					}.bind(this), duration);  
				}else{  
					setTimeout(function () {  
						uni.showModal({  
							title: '很遗憾',  
							content: '没中奖 ' + (awardsConfig.awards[awardIndex].name),  
							showCancel: false  
						});  
						this.btnDisabled= '';  
					}.bind(this), duration);  
				}  
			},
			
			getMainData() {
				const self = this;
				console.log('852369')
				const postData = {};
				postData.tokenFuncName = 'getProjectToken';
				self.$apis.orderGet(postData, callback);
			}
		}  

    }  
</script>

<style> 
 page{padding-bottom: 60rpx;}
.turntable{width: 580rpx; height: 580rpx; margin: 40rpx auto 60rpx auto;}
.turntable .pic{width: 100%; height: 100%; display: block;}

.header{  
    display: flex;  
    flex-direction: column;  
    align-items: center;  
    justify-content: center;  
    height: 100rpx;  
}  
/* 转盘 */  
.canvas-container {  
	margin:20rpx auto;  
	position: relative;  
	width: 580rpx;  
	height: 580rpx; 
	background: url(../../static/images/interactivel-img3.png) no-repeat 0 0/100% 100%;
}  
.canvas-content {  
  position: absolute;  
 /* top:50%;  
  left:50%; 
   transform: translate(-50%,-50%); */
  z-index: 1;  
  display: block;  
  width: 100%;  
  height:100%;  
  border-radius: inherit;  
  background-clip: padding-box;   
}  
.canvas-element {  
  position: relative;  
  z-index: 1;  
  width: inherit;  
  height: inherit;  
  border-radius: 50%;  
}  
.canvas-list {  
  position: absolute;  
  left: 0;  
  top: 0;  
  width: inherit;  
  height: inherit;  
  z-index: 9999;  
}  
.canvas-item {  
  position: absolute;  
  left: 0;  
  top: 0;  
  width: 100%;  
  height: 100%;
  transform: rotate(18deg);
}  
.canvas-item-text {  
  position: relative;  
  display: block;  
  padding-top: 100rpx;  
  margin: 0 auto;  
  text-align: center;  
  -webkit-transform-origin: 50% 290rpx;  
  transform-origin: 50% 290rpx;  
    display: flex;  
    flex-direction: column;  
    align-items: center;  
}  
.canvas-item-text text{  
    font-size:26rpx;
	color: #fff;
	align-items: center;-webkit-writing-mode: vertical-rl;writing-mode: vertical-rl;letter-spacing:8rpx;
}  
.canvas-item-text-img{  
    width:50rpx;  
    height:50rpx;  
    padding-top:20rpx;  
}  


.canvas-litem {  
  position: absolute;  
  left: 50%;  
  top:0;  
  transform: translate(-50%,-50%);
  width: 2rpx;  
  height: 100%;  
  background-color:#222;  
  overflow: hidden;  
}  

/**  
* 抽奖按钮  
*/  
.canvas-btn {  
	position: absolute;  
	left: 50%;  
	top: 50%;  
	z-index: 400;  
	width: 110rpx;  
	height:194rpx;
	transform: translate(-50%,-70%);
}  
.canvas-btn .btn{width: 100%;height: 100%;}

.canvas-btn.disabled {  
  pointer-events: none;  
  background: #b07a7b;  
  color: #ccc;  
}  
.canvas-btn.disabled::after {  
  border-bottom-color: #b07a7b;  
}  
.canvas-btn-table{  
    color:#A83FDB;  
    width:120rpx;  
    text-align: center;  
    position: absolute;  
    left: 240rpx;  
    top:360rpx;  
    font-size:26rpx;  
    background-color: #FFFFFF;  
    opacity: 0.9;  
}  
</style>