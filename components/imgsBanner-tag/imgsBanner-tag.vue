<template name='imgsBanner'>
		<view class="imgsBannerBox">
			<swiper class="imgsBanner_swiper" :current='comCurrentImg' @change='changCurrent'>
				<swiper-item v-for="(item,index) in imgList" :key='index' display-multiple-items="1">
					<image :src="item" mode="aspectFill"></image>
				</swiper-item>
			</swiper>
			<!-- 图片位置 -->
			<view class="imgLength">{{(comCurrentImg+1)+'/'+(imgList.length)}}</view>
			<scroll-view scroll-x="true" class="scrollImgBox" :scroll-left='scrollImgList' scroll-with-animation>
				<view class="scrollImgList">
					<image :src="item" mode="aspectFill" v-for="(item,index) in imgList" :key='index' :class="comCurrentImg==index?'activeImageItem':''" @click="onClickImg(index)" :id="'item'+index"></image>
				</view>
			</scroll-view>
		</view>
</template>

<script>
	export default {
		name:'imgsBanner',
		props:{
			imgList:{
				type:Array,
				value:[]
			},
			currentImg:{
				type:Number,
				value:0
			}
		},
		data() {
			return {
				comCurrentImg:0,
				scrollImgList:0,
				imgLeftList:[]
			};
		},
		created() {
			this.comCurrentImg = this.currentImg;
			
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
		methods:{
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
		}
	}
</script>

<style>
.imgsBannerBox{
	position: relative;
}
.imgLength{
	position: absolute;
	top: 694rpx;
	right: 24rpx;
	background:rgba(0,0,0,0.34);
	padding: 0 12rpx;
	line-height: 32rpx;
	font-size: 22rpx;
	border-radius: 16rpx;
	color: #fff;
}
.imgsBanner_swiper{
	width: 750rpx;
	height: 750rpx;
	margin-bottom: 24rpx;
}
.imgsBanner_swiper swiper-item{
	width: 750rpx;
	height: 100%;
}

.imgsBanner_swiper swiper-item image{
	width: 750rpx;
	height: 750rpx;
}


.scrollImgBox .scrollImgList{
	white-space: nowrap;
	
}
.scrollImgBox .scrollImgList image{
	width: 132rpx;
	height: 132rpx;
	margin-right: 16rpx;
	display: inline-block;
	border: 6rpx solid #fff;
}
.scrollImgBox .scrollImgList image:last-child{
	margin-right: 0;
}
.scrollImgBox .scrollImgList .activeImageItem{
	border: 6rpx solid #F57341;
}

</style>
