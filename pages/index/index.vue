<template>
	<view class="page">
		<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000" class="carousel">
			<swiper-item v-for="(item, index) in carouselList" :key="index">
				<view class="swiper-item">
					<image :src="item.image" mode="" class="carousel"></image>
				</view>
			</swiper-item>
		</swiper>
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
				url: 'http://192.168.1.101:8000/index/carousel/list.json', //仅为示例，并非真实接口地址。
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
