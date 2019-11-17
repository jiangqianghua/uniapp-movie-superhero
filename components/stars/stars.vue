<template>
	<view class="movie-scroe-wapper">
		<image v-for="yellow in yellowScore" src="../../static/icos/star-yellow.png" class="star-ico"></image>
		<image v-for="gray in grayScore" src="../../static/icos/star-gray.png" class="star-ico"></image>
		<view class="movie-scroe" v-show="showScore == 1">
			{{score}}
		</view>
	</view>
</template>

<script>
export default {
	name: 'stars',
	props: {
		score: 0,
		showScore: 0
	},
	created() {
		let tempScore = 0
		if ( this.score != null && this.score != undefined && this.score != '' ) {
			tempScore = this.score
		}
		let yellowScore = parseInt(tempScore / 2)
		let grayScore = 5 - yellowScore
		this.yellowScore = yellowScore
		this.grayScore = grayScore
		
	},
	data() {
		return {
			yellowScore: 0,
			grayScore: 5
		}
	}
}
</script>

<style scoped>
	.movie-scroe-wapper{
		display: flex;
		flex-direction: row;
		align-items: center;
	}
	.star-ico{
		width: 20upx;
		height: 20upx;
		margin-top: 6upx;
	}
	.movie-scroe{
		font-size: 12px;
		color: grey;
		margin-left: 8upx;
	}
</style>
