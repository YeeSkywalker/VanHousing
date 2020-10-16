<template>
	<view>
		<view  :animation="anData"  style="height:0;">
		</view>
		<scroll-view scroll-with-animation scroll-y="true"  @touchmove="hideKey"
		style="width: 750rpx;" :style="{'height':srcollHeight}" :scroll-top="go" >
			<view id="okk" scroll-with-animation >
			<view  class="flex-column-start" v-for="(x,i) in msgList" :key="i">
				<view v-if="x.my" class="flex justify-end padding-right one-show  align-start  padding-top" >
					<view class="flex justify-end"  style="width: 400rpx;">
						<view class="margin-left padding-chat bg-navy" style="border-radius: 35rpx;">
							<text style="word-break: break-all;">{{x.msg}}</text>
						</view>
					</view>
	
				</view>
				<view v-if="!x.my" class="flex-row-start margin-left margin-top one-show" >
					<view class="chat-img flex-row-center">
						<image style="height: 75rpx;width: 75rpx;" src="../../static/img/robt.png" mode="aspectFit"></image>
					</view>
					<view  class="flex"  style="width: 500rpx;">
						<view class="margin-left padding-chat flex-column-start" style="border-radius: 35rpx;background-color: #f9f9f9;">
							<text  style="word-break: break-all;" >{{x.msg}}</text>
							<view class="flex-column-start" v-if="x.type==1" style="color: #3d7cc8;">
								<text style="color: #838383;font-size: 22rpx;margin-top: 15rpx;">We got u!</text>
								<text @click="answer(index)" style="margin-top: 30rpx;" 
								v-for="(item,index) in x.questionList" :key="index" >{{item}}</text>
								<view class="flex-row-start  padding-top-sm">
								</view>
							</view>
					
							<view class="flex-column-start" v-if="x.type==2" style="color: #3d7cc8;">
								<text style="color: #838383;font-size: 22rpx;margin-top: 15rpx;">Maybe you have question like these?</text>
								<text @click="answer(index)" style="margin-top: 30rpx;" 
								v-for="(item,index) in x.questionList" :key="index" >{{item}}</text>
							</view>

							<view class="flex-column-start" v-if="x.type==0">
								<text class="padding-top-sm" style="color: #3d7cc8;">Report this issue!</text>	
							</view>
							
							
						</view>
					</view>
				</view>
		</view>
		<view v-show="msgLoad" class="flex-row-start margin-left margin-top">
			<view class="chat-img flex-row-center">
				<image style="height: 75rpx;width: 75rpx;" src="../../static/img/robt.png" mode="aspectFit"></image>
			</view>
			<view  class="flex"  style="width: 500rpx;">
				<view class="margin-left padding-chat flex-column-start" 
				style="border-radius: 35rpx;background-color: #f9f9f9;">
					<view class="cuIcon-loading turn-load" style="font-size: 35rpx;color: #3d7cc8;">
						
					</view>
				</view>
			</view>	
		</view>
		<view style="height: 120rpx;"></view>
		</view>	
	
		</scroll-view>		
		<view class="flex-column-center" style="position: fixed;bottom: -130px;"
		:animation="animationData" >		
			<view class="bottom-dh-char flex-row-around" style="font-size: 55rpx;">
				 <input  v-model="msg"  class="dh-input" type="text" style="background-color: #dbdde3;" 
				 @confirm="sendMsg" confirm-type="search" placeholder-class="my-neirong-sm"
				 placeholder="Let's Chat!" /> 
				 <view @click="sendMsg" class="cu-tag bg-navy round">
				 	Send
				 </view>
				<text @click="ckAdd" class="cuIcon-roundaddfill text-orange"></text>
			</view>		
			<view class="box-normal flex-row-around flex-wrap">
			</view>
		</view>	
	</view>
</template>

<script>
	var l
	var wh
	var mgUpHeight
	export default {	
		onLoad(){
			uni.onKeyboardHeightChange(res => {
				const query = uni.createSelectorQuery()
				query.select('#okk').boundingClientRect(data => {
					var up=res.height*2-data.height-l*110
					console.log(up)
				  if(up>0){
					 this.msgMove(up,300)
					 mgUpHeight=up
				  }
				  if(res.height==0){
					   this.msgMove(0,0)	
				  }
				}).exec();
			 })
			var query=uni.getSystemInfoSync()
						
			l=query.screenWidth/750		
			wh=query.windowHeight								
			this.srcollHeight=query.windowHeight+"px"
		},
		data() {
			return {
				msgLoad:false,
				anData:{},
				animationData:{},
				showTow:false,
				msgList:[{my:false,msg:"Hello There!",
				type:1,questionList:["My Property status?","Agent Recommand!"]}],
				msg:"",
				go:0,
				srcollHeight:0
			}
		},
		methods: {
			goPag(kh){	
				this.upTowmn(0,250)
				if(this.keyHeight!=0){					
					if(kh-this.keyHeight>0){
						this.upTowmn(this.keyHeight-kh,250)
					}
					
				}
			},
			msgMove(x,t){
				var animation = uni.createAnimation({
				        duration: t,
				          timingFunction: 'linear',
				      })
				  
				      this.animation = animation
				  
				      animation.height(x).step()
				  
				      this.anData = animation.export()
			},
			msgGo(){
				const query = uni.createSelectorQuery()
				setTimeout(()=>{
					query.select('#okk').boundingClientRect(data => {
					   if(data.height-wh>0){
						   this.go=data.height-wh
						   
					   }
					   var moveY=wh-data.height
					   
					   if(moveY-mgUpHeight<0){
						   if(moveY<0){
							   this.msgMove(0,200)
						   }else{
							  this.msgMove(moveY,200) 
						   }					   
					   }
						
					}).exec();
				},100)
			},
			
			answer(id){
				console.log(id)	
			},
			sendMsg(){
				
				if(this.msg==""){
					return 0;
				}
				this.msgList.push({"msg":this.msg,"my":true})				
				this.msgGo()
				this.msgKf(this.msg)
				this.msg=""
			},
			msgKf(x){				
				this.msgLoad=true
				setTimeout(()=>{
					this.msgLoad=false
					this.msgList.push({my:false,msg:"Sorry, you know nothing John Snow! T^T"})
					this.msgGo()
				},100)
			},
			ckAdd(){
				if(!this.showTow){
					this.upTowmn(-180,350)
				}else{
					this.upTowmn(0,200)
				}
				this.showTow=!this.showTow
			},
			hideKey(){
				uni.hideKeyboard()
			},
			upTowmn(x,t){
				
				 var animation = uni.createAnimation({
				      duration: t,
				        timingFunction: 'ease',
				    })
				 				
				    this.animation = animation
				 				
				    animation.translateY(x).step()
				 				
				    this.animationData = animation.export()
			}
		}
	}
</script>

<style>
.bottom-dh-char{
	 	background-color: #f9f9f9;
	 	width: 750rpx;
	 	height: 110rpx;
	 }
.center-box{
	width: 720rpx;
	padding-left: 25rpx;
}
.hui-box{
	width: 750rpx;
	height: 100%;
	
}
.dh-input{
	width: 500rpx;
	height: 65rpx;
	border-radius: 30rpx;
	padding-left: 15rpx;
	background-color: #FFFFFF;
}
.box-normal{
	width: 750rpx;
	height: 180px;
	background-color: #FFFFFF;
}
.tb-text view{
	font-size: 65rpx;
}
.tb-text text{
	font-size: 25rpx;
	color: #737373;
}
.chat-img{
	border-radius: 50%;
	width: 100rpx;
	height: 100rpx;
	background-color: #f7f7f7;
}

.padding-chat{
	padding: 17rpx 20rpx;
}
.tb-nv{
	width: 50rpx;
	height: 50rpx;
}
.flex-column-center{
	bottom: 260rpx;
}
</style>
