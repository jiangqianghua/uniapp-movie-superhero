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
				trailerList: []
			}
		},
		onLoad() {
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

		}
	}
</script>

<style>
	@import url("index.css");
</style>
