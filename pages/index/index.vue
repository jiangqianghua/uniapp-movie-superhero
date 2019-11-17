<template>
	<view class="page">
		<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000" class="carousel">
			<swiper-item v-for="(item, index) in carouselList" :key="index">
				<view class="swiper-item">
					<image :src="item.image" mode="" class="carousel"></image>
				</view>
			</swiper-item>
		</swiper>
		
		<view class="page-block super-hot">
			<view class="hot-title-wapper">
				<image src="../../static/icos/hot.png" class="hot-ico"></image>
				<view class="hot-title">
					热门超英
				</view>
			</view>
		</view>
		<scroll-view class="page-block hot" scroll-x="true">
			<view class="single-poster" v-for="(item, index) in hotSuperroList" :key="index">
				<view class="poster-wapper">
					<image :src="item.cover" class="poster"></image>
					<view class="movie-name">
						{{item.name}}
					</view>
					<stars :score="item.score" :showScore="1"></stars>
				</view>
			</view>
		</scroll-view>
		
		<view class="page-block super-hot">
			<view class="hot-title-wapper">
				<image src="../../static/icos/interest.png" class="hot-ico"></image>
				<view class="hot-title">
					热门预告
				</view>
			</view>
		</view>
		<view class="hot-movies page-block">
			<video v-for="trailer in trailerList"
			:src="trailer.trailer"
			:poster="trailer.poster"
			class="hot-movie-single"
			></video>
		</view>
		
		<view class="page-block super-hot">
			<view class="hot-title-wapper">
				<image src="../../static/icos/guess-u-like.png" class="hot-ico"></image>
				<view class="hot-title">
					猜你喜欢
				</view>
			</view>
		</view>
		
		<view class="page-block guess-u-like">
			<view class="single-like-movie">
				<image :src="'http://192.168.1.102:8000/imgs/poster/civilwar.jpg'" class="like-movie"></image>
				<view class="movie-desc">
					<view class="movie-title">
						蝙蝠大战超人2333344
					</view>
					<stars :score="5" :showScore="0"></stars>
					<view class="movie-info">
						2018 /  美国 / 科幻 动作
					</view>
					<view class="movie-info">2018 /  美国 / 科幻 动作</view>
				</view>
				<view class="movie-oper" @click="praiseMe">
					<image src="../../static/icos/praise.png" class="praise-ico"></image>
					<view class="praise-me">
						点赞
					</view>
					<view :animation="animationData" class="praise-me animation-opacity">
						+1
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import stars from '../../components/stars/stars'
	export default {
		components: {
			stars
		},
		data() {
			return {
				carouselList: [],
				hotSuperroList: [],
				trailerList: [],
				animationData: {}
			}
		},
		onUnload() {
			this.animationData = {}
		},
		onLoad() {
			
			this.animation = uni.createAnimation()
			
			uni.request({
				url: this.serverUrl+'/index/carousel/list.json', 
				success: (res) => {
					if (res.data.status == 200){
						this.carouselList = res.data.data
					}
				}
			});
			uni.request({
				url: this.serverUrl+'/index/hotdata.json', 
				success: (res) => {
					if (res.data.status == 200){
						this.hotSuperroList = res.data.data
					}
				}
			});
			uni.request({
				url: this.serverUrl+'/index/trailer.json', 
				success: (res) => {
					if (res.data.status == 200){
						this.trailerList = res.data.data
					}
				}
			});
		},
		methods: {
			praiseMe() {
				this.animation.translateY(-60).opacity(1).step({
					duration:400
				})
				this.animationData = this.animation.export()
				
				setTimeout(function() {
					// 还原动画
					this.animation.translateY(0).opacity(0).step({
						duration:0
						})
					this.animationData = this.animation.export()
				}.bind(this), 800);
			}
		}
	}
</script>

<style>
	@import url("index.css");
</style>
