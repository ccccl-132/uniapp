<template>
	<view class="container">
		<view class="inv-h-w">
		        <view :class="['inv-h',Inv==0?'inv-h-se':'']" @click="Inv=0">全部</view>
		        <view :class="['inv-h',Inv==1?'inv-h-se':'']" @click="Inv=1">待选</view>
				<view :class="['inv-h',Inv==2?'inv-h-se':'']" @click="Inv=2">面试中</view>
				<view :class="['inv-h',Inv==3?'inv-h-se':'']" @click="Inv=3">通过</view>
				<view :class="['inv-h',Inv==4?'inv-h-se':'']" @click="Inv=4">失败</view>
		</view>
		<!-- <view class="" v-show="Inv == 0"> -->
		        <view class="zong" v-show="Inv == 0" @click="resumeDetails(item)" v-for="(item, index) in infoList" :key="index">
					<view class="zong-top">
						求阿里、百度的内推，谢谢各位大佬
					</view>
					<view class="jianli">
						<view class="jianli-left">
							<image class="item-img" src="http://112.74.58.46:8103/uploads/icon/1.png">
						</view>
						<view class="jianli-right">
							<!-- <image class="item-img" src="http://112.74.58.46:8103/uploads/icon/1.png"> -->
							<view class="tex tex1">{{item.name}}</view>
							<view class="tex">{{item.graduationSchool}}</view>
							<view class="tex">实习经历：{{item.internshipExperience}}</view>
						</view>
					</view>
		        </view>
		<!-- </view> -->
		<!-- <view class="" v-show="Inv == 1"> -->
		        <view class="zong" v-show="Inv == 1" @click="resumeDetails(item)" v-for="(item, index) in infoListtwo" :key="'info2-'+index">
		        	<view class="zong-top">
		        		求阿里、百度的内推，谢谢各位大佬
		        	</view>
		        	<view class="jianli">
		        		<view class="jianli-left">
		        			<image class="item-img" src="http://112.74.58.46:8103/uploads/icon/1.png">
		        		</view>
		        		<view class="jianli-right">
		        			<!-- <image class="item-img" src="http://112.74.58.46:8103/uploads/icon/1.png"> -->
		        			<view class="tex tex1">{{item.name}}</view>
		        			<view class="tex">{{item.graduationSchool}}</view>
		        			<view class="tex">实习经历：{{item.internshipExperience}}</view>
		        		</view>
		        	</view>
		        </view>
		<!-- </view> -->
		<view class="" v-show="Inv == 2">
		        我是选项卡三
		</view>
		<view class="" v-show="Inv == 3">
		        我是选项卡四
		</view>
		<view class="" v-show="Inv == 4">
		        我是选项卡五
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				Inv:0,
				name:'',
				graduationSchool:'',
				internshipExperience:'',
				infoList:[],
				infoListtwo:[],
				id:'',
				memberId:59,
				recruitld:1,
				// item.icon:require(),
				// item:require('./uploads/icon/defaultIcon.png'),
			}
		},
		methods: {
			changeTab(Inv){
			        that.navIdx = Inv;
			         
			},
			getInfoList(){
				this.$u.get('http://112.74.58.46:8103/resume/info/selectAllResumeList', {
						recruitId:1,
						memberId:59
					}).then(res => {
						console.log(res);
						this.infoList=res;
						// console.log(this.infoList.length);
						for( var i=0;i<=this.infoList.length;i++){
							if(this.infoList[i].type==1){
								this.infoListtwo.push(this.infoList[i]);
								console.log(this.infoList[i]);
							}
						}
				});
			},
			onLoad(){
				this.getInfoList();
			},
			resumeDetails(index){//简历详情
				console.log(index);
				var listData = JSON.stringify(index);
				uni.navigateTo({
				    url: '../resumeDetails/resumeDetails?listData='+listData
				});
			},
			
			
		}
	}
</script>

<style>
	.inv-h-w{
		background-color: #FFFFFF;
		height: 100upx;
		width: 750upx;
		display: flex;
	}
	.inv-h{
		font-size: 30upx;
		flex: 1;
		text-align: center;
		color: #C9C9C9;
		height: 100upx;
		line-height: 100upx;
	}
	.inv-h-se{
		color: #5BA7FF;
		border-bottom: 4upx solid #5BA7FF;
	}
	page{
		background-color: #F2F2F2;
	}
	.zong{
		background-color: #ffffff;
		height: 120px;
		margin-top: 10pt;
	}
	.zong-top{
		height: 30px;
		padding-left: 15px;
		font-size: 20px;
		font-weight: 900;
	}
	.jianli{
		padding-left: 10px;
	}
	.jianli-left{
		height: 100px;
		width: 90px;
		/* background-color: #007AFF; */
		float: left;
		position: relative;
	}
	.jianli-right{
		height: 100px;
		width: 265px;
		padding-top: 5px;
		/* background-color: #4CD964; */
		float: left;
	}
	.tex{
		margin-bottom: 5px;
	}
	.item-img{
		width: 70px;
		height: 70px;
		border-radius: 10px;
		position: absolute;
		bottom: 25px;
		left: 10px;
	}
	.tex1{
		/* font-family: PingFangSC-Medium;
		font-size: medium; */
		font-size: 15px;
		font-weight: 900;
		color: #333333;
	}
</style>
