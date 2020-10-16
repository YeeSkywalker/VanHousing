<template>
	<view>
		<view class="page-body">
		    <view class="page-section page-section-gap">
		       <map style="width: 100%; height: 1146rpx;" :latitude="latitude" :longitude="longitude" :markers="covers" show-location="true"   :scale="num" >
		        </map>
		    </view>
		</view>
	</view>
</template>
<script>
	export default {
		data() {
			return {
				showImage: false,
				itemList: [],
				num:16,
				title: 'map',
				latitude: 26.0745,
				longitude: 119.2965,
				covers: [{
				    latitude: 49.275531,
				    longitude:-123.114621,
				    iconPath: '../../static/img/position.png',
					iconPath:"",
				}]
			}
		},
		onLoad(){
			this.getList();
			this.showImage = true;
		},
		methods: {
			getList(){
				uni.request({
					url:'../../static/data.json',
					success: (res) => {
						console.log(res.data);
						this.itemList = res.data.result.data
					}
				})
			},
			openLocation: function (e) {
				var value = e.detail.value
				uni.openLocation({
					longitude: Number(value.longitude),
					latitude: Number(value.latitude),
					name: value.name,
					address: value.address
				})
			}
		}
	}
</script>
<style>
	map {
		align-self: center;
		width: 100%;
		height: 700rpx;
	}
	.mapSpace{
		padding-left: 30rpx;
		padding-right:30rpx;
		padding-top: 30rpx;
		padding-bottom: 30rpx;
	}
	.uni-list-cell-left {
		padding: 0 30rpx;
	}
	.img-container{
		font-size: 1;
	}
	.img-container img{
		width: auto;
		height: auto;
		max-width: 100%;
		max-height: 100%;
	}
</style>
