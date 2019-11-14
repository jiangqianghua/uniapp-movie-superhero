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
			<view class="single-poster">
				<view class="poster-wapper">
					<image src="../../static/poster/civilwar.jpg" class="poster"></image>
					<view class="movie-name">
						344445556664445556
					</view>
					<view class=""></view>
				</view>
			</view>
			<view class="single-poster">
				<view class="poster-wapper">
					<image src="../../static/poster/civilwar.jpg" class="poster"></image>
					<view class="movie-name">
						34444555666
					</view>
					<view class=""></view>
				</view>
			</view>
			<view class="single-poster">
				<view class="poster-wapper">
					<image src="../../static/poster/civilwar.jpg" class="poster"></image>
					<view class="movie-name">
						34444555666
					</view>
					<view class=""></view>
				</view>
			</view>
			<view class="single-poster">
				<view class="poster-wapper">
					<image src="../../static/poster/civilwar.jpg" class="poster"></image>
					<view class="movie-name">
						34444555666
					</view>
					<view class=""></view>
				</view>
			</view>
			<view class="single-poster">
				<view class="poster-wapper">
					<image src="../../static/poster/civilwar.jpg" class="poster"></image>
					<view class="movie-name">
						34444555666
					</view>
					<view class=""></view>
				</view>
			</view>
			<view class="single-poster">
				<view class="poster-wapper">
					<image src="../../static/poster/civilwar.jpg" class="poster"></image>
					<view class="movie-name">
						34444555666
					</view>
					<view class=""></view>
				</view>
			</view>
			<view class="single-poster">
				<view class="poster-wapper">
					<image src="../../static/poster/civilwar.jpg" class="poster"></image>
					<view class="movie-name">
						34444555666
					</view>
					<view class=""></view>
				</view>
			</view>
			<view class="single-poster">
				<view class="poster-wapper">
					<image src="../../static/poster/civilwar.jpg" class="poster"></image>
					<view class="movie-name">
						34444555666
					</view>
					<view class=""></view>
				</view>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				carouselList: []
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
		},
		methods: {

		}
	}
</script>

<style>
	@import url("index.css");
</style>
