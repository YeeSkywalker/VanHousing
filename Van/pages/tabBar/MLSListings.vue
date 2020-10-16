<template>
	<view>
		<view class="MLS-tab-section">
			<view class="MLS-tab" @tap="areaTap">Area</view>
			<view class="MLS-tab" @tap="typeTap">Type</view>
			<view class="MLS-tab" @tap="priceTap">Price</view>
			<view class="MLS-tab" @tap="sortTap">Sort</view>
		</view>
		<view class="img-container" @click="goToPage">
			<img src="../../static/img/House1.jpeg">
		</view>
		<view class="img-container">
			<img src="../../static/img/House2.jpeg">
		</view>
		<view class="img-container">
			<img src="../../static/img/House3.jpeg">
		</view>
	</view>
</template>

<script>
	export default{
		methods:{
			areaTap(){
				uni.showActionSheet({
					title:'全部 ALL',
					itemList: ['温西 Vancouver West', '温东 Vancouver East', 
					'温市中心 Vancouver Downtown', '西温 West Vancouver', '北温 North Vancouver',
					'列治文 Richmond', '本拿比 Burnaby', '高贵林 Coquitlam', '高贵林港 Port Coquitlam']
				})
			},
			typeTap(){
				uni.showActionSheet({
					title: '全部 ALL',
					itemList: ['独立屋 House', '联排别墅 Townhouse', '公寓 Apartment', '双拼屋 Duplex']
				})
			},
			priceTap(){
				uni.showActionSheet({
					itemList: ['Below $1,000,000','$1,000,000 to $2,000,000', '$2,000,000 to $3,000,000',
					'Above $3,000,000']
				})
			},
			sortTap(){
				uni.showActionSheet({
					itemList: ['默认排序 Default', '价格从高到低 $High - Low', '价格从低到高 $Low - High']
				})
			},
			goToPage(){
				uni.navigateTo({
					url: "./House"
				})
			}
		}
	}
</script>

<style>
	.MLS-tab-section{
		display: flex;
		
	}
	.MLS-tab{
		padding-top: 2vw;
		padding-bottom: 2vw;
		width: 25%;
		text-align: center;
		font-size: 4vw;
		background-color: #d5d3d8;		
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
