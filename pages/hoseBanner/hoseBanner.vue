<template>
	<view>
		<view class="headTit flexCenter white fs16 pr">
			<view class="backBtn" @click="back()"><image src="../../static/images/back-icon.png" mode=""></image></view>
			<view>{{(comCurrentImg+1)+'/'+(imgList.length)}}</view>
		</view>
		<view class="banner-box">
			<swiper  class="swiper-box" :current='comCurrentImg' @change='changCurrent'>
				<swiper-item  class="swiper-item white" v-for="(item,index) in imgList" :key='index' display-multiple-items="1">
					<image :src="item" class="slide-image" />
				</swiper-item>
			</swiper>
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
				imgList:[
					"../../static/images/door-modell-img.png",
					"../../static/images/door-modell-img.png",
					"../../static/images/door-modell-img.png",
					"../../static/images/door-modell-img.png"
				],
				currentImg:0,  //当前默认选中
				comCurrentImg:0,
				scrollImgList:0,
				imgLeftList:[]
			}
		},
		onLoad() {
			const self = this;
			//self.$Utils.loadAll(['getMainData'], self);
		},
		mounted() {
			uni.getSystemInfo({
			    success: (res)=> {
					this.imgList.forEach((i,v)=>{
						let info = uni.createSelectorQuery().in(this);
						info.select("#item"+v).boundingClientRect((res)=>{
						    this.imgLeftList.push(res.left)
						}).exec()
					})
					this.imgListScroll(this.comCurrentImg)
			    }
			});
		},
		methods: {
			back(){
				const self = this;
				self.$router.go(-1)
			},
			onClickImg(index){
				this.comCurrentImg = index
				this.imgListScroll(index)
			},
			changCurrent(e){
				this.comCurrentImg = e.target.current
				this.imgListScroll(e.target.current)
			},
			// 图片滑动
			imgListScroll(index){
				if(index>=2){
					this.scrollImgList = this.imgLeftList[index-2]
				}else{
					this.scrollImgList = 0
				}
			}

		},
	};
</script>

<style>
	page{background: #222;}	
	
	.backBtn{width:20rpx;height: 35rpx;position: absolute;top: 50%;left: 30rpx;transform: translateY(-50%);}
	.headTit{height: 88rpx;line-height: 88rpx;background: #222;}
	
	/* .banner-box{width: 100%;height: 800rpx;} */
	.banner-box{width: 640rpx;height: 1021rpx;overflow: hidden;margin: 0 auto;margin-top: 80rpx;}
	.swiper-box {height: 100%;box-sizing: border-box;}
	.swiper-box swiper-item{width: 100%;box-sizing: border-box;overflow: hidden;}
	.swiper-box swiper-item image {width: 100%;height: 100%;box-sizing: border-box;}
	
	/* .banner-box{width: 100%;height: 800rpx;}
	.swiper-box {height: 100%;box-sizing: border-box;}
	.swiper-box swiper-item{width: 100%;box-sizing: border-box;overflow: hidden;}
	.swiper-box swiper-item .pic{width: 100%;height: 450rpx;box-sizing: border-box;}
	.swiper-box swiper-item .text2{font-size: 30rpx;line-height: 50rpx;} */
	.imgLength{position: fixed; bottom: 20%;right: 30rpx; z-index: 22;width: 70rpx;height: 70rpx;border-radius: 50%;background: #fff;text-align: center;line-height: 70rpx;font-size: 26rpx;}
	
</style>
