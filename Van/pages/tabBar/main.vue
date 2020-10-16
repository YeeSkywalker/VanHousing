<template>
	<view class="uni-flex uni-column">
		
		<view class="tab-container">
			<view class="tab">
			　	<option @tap="change(0)" :class="{btna:btnnum == 0}">Buy</option>
				<option @tap="change(1)" :class="{btna:btnnum == 1}">Rent</option>
			　	<option @tap="change(2)" :class="{btna:btnnum == 2}">Service</option>
			</view>
			
			<view class="end-cont" :class="{dis:btnnum == 0}">
			 　　<view class="tab-page">
					<view class="choice-block">
						<image class="icon-image" src="../../static/img/MLS.png" @click="goToMLS"></image>
						<text class="icon-text">MLS® Listings</text>
					</view>
					<view class="choice-block">
						<image class="icon-image" src="../../static/img/Investment.png"></image>
						<text class="icon-text">Investment</text>
					</view>
					<view class="choice-block">
						<image class="icon-image" src="../../static/img/Developments.png"></image>
						<text class="icon-text">Developments</text>
					</view>
					<view class="choice-block">
						<image class="icon-image" src="../../static/img/Open.png"></image>
						<text class="icon-text">Open</text>
					</view>
				</view>
				<view class="tab-page">
					<view class="choice-block">
						<image class="icon-image" src="../../static/img/Trends.png"></image>
						<text class="icon-text">Trends</text>
					</view>
					<view class="choice-block">
						<image class="icon-image" src="../../static/img/Price.png"></image>
						<text class="icon-text">Price Changes</text>
					</view>
					<view class="choice-block">
						<image class="icon-image" src="../../static/img/School.png"></image>
						<text class="icon-text">Schools</text>
					</view>
					<view class="choice-block">
						<image class="icon-image" src="../../static/img/View.png"></image>
						<text class="icon-text">Most Viewed</text>
					</view>
				</view>
			</view>
			
			<view class="end-cont" :class="{dis:btnnum == 1}">
			 　　<view class="tab-page">
					<view class="choice-block">
						<image class="icon-image" src="../../static/img/LongTerms.png"></image>
						<text class="icon-text">LongTerms</text>
					</view>
					<view class="choice-block">
						<image class="icon-image" src="../../static/img/ShortTerm.png"></image>
						<text class="icon-text">ShortTerm</text>
					</view>
					<view class="choice-block">
						<image class="icon-image" src="../../static/img/Commercial.png"></image>
						<text class="icon-text">Commercial</text>
					</view>
					<view class="choice-block">
						<image class="icon-image" src="../../static/img/Homestay.png"></image>
						<text class="icon-text">Homestay</text>
					</view>
				</view>
				<view class="tab-page">
					<view class="choice-block">
						<image class="icon-image" src="../../static/img/Rent.png"></image>
						<text class="icon-text">Post Ad</text>
					</view>
					<view class="choice-block">
						<image class="icon-image" src="../../static/img/Market.png"></image>
						<text class="icon-text">Market Report</text>
					</view>
					
				</view>
			</view>
			<view class="end-cont" :class="{dis:btnnum == 2}">
				<view class="tab-page">
					<view class="choice-block">
						<image class="icon-image" src="../../static/img/Services.png"></image>
						<text class="icon-text">House Services</text>
					</view>
					<view class="choice-block">
						<image class="icon-image" src="../../static/img/Zoning.png"></image>
						<text class="icon-text">Zoning Info</text>
					</view>
					<view class="choice-block">
						<image class="icon-image" src="../../static/img/Release.png"></image>
						<text class="icon-text">Service Ad</text>
					</view>
		
				</view>
			</view>
		</view>
		<view class="mini-tab-section">
			<view class="mini-tab">
			　	<mini-tab-button @tap="tabChange(0)" :class="{buttonSelected:tabNum == 0}">My interest</mini-tab-button>
				<mini-tab-button @tap="tabChange(1)" :class="{buttonSelected:tabNum== 1}">Friend Rec</mini-tab-button>
			</view>
		</view>
		<view class="text-box" >
			<text>YeeSkywalker Pressent</text>
		</view>
	</view>
	
</template>

<script>
	export default{
		data() {
		   return {
		      btnnum: 0,
			  tabNum: 0,
		   };
		},
		methods:{
			change(e) {
				this.btnnum = e
				console.log(this.btnnum)
			},
			tabChange(a){
				this.tabNum = a
				console.log(this.tabNum)
			},
			goToMLS(){
				uni.navigateTo({
					url:"./MLSListings"
				})
			}
		  
		}
	}
	
</script>

<style>
	.image-container{
		font-size: 0;
	}
	.image-container img{
		width: auto;
		height: auto;
		max-width: 100%;
		max-height: 100%;
	}
	.tab-container{
		margin: 20rpx 50rpx 50rpx;
		border: #bab9c3;
		border-style: solid;
		border-width: thin;
	}
    .tab{
        display: flex;
		flex-wrap: wrap;
		background: #bab9c3;
		color: #444a4b;
		font-family:Arial,Helvetica,sans-serif;
		font-size: 30rpx;
    }
    .tab option{
        flex-grow: 1;
        text-align: center;
    }
    .end-cont{
        display: none;
		font-family:Arial,Helvetica,sans-serif;
        background: #FFFFFF;
    }
    .btna{
        color: #3d7cc8;
        background: #FFFFFF;
    }
    .dis{
        display: block;
    }
	.tab-page{
		display: flex;
	}
	.choice-block{
		padding-top: 20upx;
		width: 25%;
		height: 15vw;
		display: flex;
		flex-direction: column;
		align-items: center;	
	}
	.icon-image{
		width: 64upx;
		height: 64upx;
	}
	.icon-text{
		color: #bab9c3;
		font-size: 20rpx;
	}
	.mini-tab-section{
		margin: 20rpx 200rpx 100rpx;
		border: #bab9c3;
		border-style: solid;
		border-width: thin;
		border-radius: 20rpx;
	}
	.mini-tab{
	    display: flex;
		flex-wrap: wrap;
		background: #FFFFFF;
		color: #3D7CC8;
		font-family:Arial,Helvetica,sans-serif;
		font-size: 30rpx;
		border-radius: 20rpx;
	}
	.mini-tab mini-tab-button{
	    flex-grow: 1;
	    text-align: center;
	}
	.buttonSelected{
		color: #FFFFFF;
		background: #3d7cc8;
		border-radius: 20rpx;
	}
	.text-box{
		padding-left:50upx;
		padding-right:50upx;
		font-size: 20rpx;
		color: #bab9c3;
	}
	
</style>
