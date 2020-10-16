<template>
	<view>
		<view class="sample-container">
			<img src="../../static/img/Sample1.jpeg">
		</view>
		<view class="sample-container">
			<img src="../../static/img/Sample4.jpeg">
		</view>
		<view class="sample-container">
			<img src="../../static/img/Sample5.jpeg">
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				info:[{
					url: 'file:///Users/yeeskywalker/Documents/HBuilderProjects/eeWghdc/static/img/Sample1.jpeg'
				},{
					url: 'static/img/Sample2.jpeg'
				},{
					url: 'static/img/Sample3.jpeg'
				},
				],
				
				dotStyle:{
					backgroundColor: 'rgba(0, 0, 0, .3)',
					border: '1px rgba(0, 0, 0, .3) solid',
					color: '#fff',
					selectedBackgroundColor: 'rgba(0, 0, 0, .9)',
					selectedBorder: '1px rgba(0, 0, 0, .9) solid'
				},
				
				modeIndex: -1,
				styleIndex: -1,
				current: 0,
				mode: 'default',
			}
		}
	}
</script>

<style>
	.sample-container{
		font-size: 0;
	},
	.sample-container img{
		width: auto;
		height: auto;
		max-width: 100%;
		max-height: 100%;
	}
</style>
