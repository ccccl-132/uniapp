<template>
	<view class="wai" style="width: 750px;
height: 2130px;
">
		<view class="jianlixiangqing">简历详情</view>
		<view class="kk">

		</view>

		<image class="item-img" src="http://112.74.58.46:8103/uploads/icon/1.png">
			<view class="listDataName">


				{{listData.name}}</view>
			<view class="listDataGraduationSchool">


				{{listData.graduationSchool}}</view>
			<view class="ll">

			</view>
			<svg t="1604758201026" class="icon1" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="3947"
			 width="200" height="200" style="width: 26rpx;
height: 30rpx;

">
				<path d="M699.733333 1024h-375.466666C259.413333 1024 204.8 969.386667 204.8 904.533333v-785.066666C204.8 54.613333 259.413333 0 324.266667 0h375.466666C764.586667 0 819.2 54.613333 819.2 119.466667v785.066666c0 64.853333-54.613333 119.466667-119.466667 119.466667zM324.266667 34.133333C276.48 34.133333 238.933333 71.68 238.933333 119.466667v785.066666C238.933333 952.32 276.48 989.866667 324.266667 989.866667h375.466666c47.786667 0 85.333333-37.546667 85.333334-85.333334v-785.066666C785.066667 71.68 747.52 34.133333 699.733333 34.133333h-375.466666z"
				 fill="" p-id="3948"></path>
				<path d="M802.133333 170.666667h-580.266666c-10.24 0-17.066667-6.826667-17.066667-17.066667s6.826667-17.066667 17.066667-17.066667h580.266666c10.24 0 17.066667 6.826667 17.066667 17.066667s-6.826667 17.066667-17.066667 17.066667zM785.066667 853.333333H238.933333c-10.24 0-17.066667-6.826667-17.066666-17.066666s6.826667-17.066667 17.066666-17.066667h546.133334c10.24 0 17.066667 6.826667 17.066666 17.066667s-6.826667 17.066667-17.066666 17.066666zM597.333333 102.4h-170.666666c-10.24 0-17.066667-6.826667-17.066667-17.066667s6.826667-17.066667 17.066667-17.066666h170.666666c10.24 0 17.066667 6.826667 17.066667 17.066666s-6.826667 17.066667-17.066667 17.066667zM699.733333 102.4c-10.24 0-17.066667-6.826667-17.066666-17.066667s6.826667-17.066667 17.066666-17.066666 17.066667 6.826667 17.066667 17.066666-6.826667 17.066667-17.066667 17.066667z"
				 fill="" p-id="3949"></path>
				<path d="M512 921.6m-34.133333 0a34.133333 34.133333 0 1 0 68.266666 0 34.133333 34.133333 0 1 0-68.266666 0Z" fill=""
				 p-id="3950"></path>
			</svg>
			<svg t="1604759419530" class="icn2" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="8043"
			 width="200" height="200" >
				<path d="M928 160H96c-17.7 0-32 14.3-32 32v640c0 17.7 14.3 32 32 32h832c17.7 0 32-14.3 32-32V192c0-17.7-14.3-32-32-32z m-80.8 108.9L531.7 514.4c-7.8 6.1-18.7 6.1-26.5 0L189.6 268.9c-1.8-1.4-2.8-3.5-2.8-5.7 0-4 3.2-7.2 7.2-7.2h648.8c2.2 0 4.3 1 5.7 2.8 2.4 3.1 1.9 7.6-1.3 10.1z"
				 p-id="8044"></path>
			</svg>
			<view class="qiuneitui">求内推信息</view>
				<view class="qiugongsi">求内推公司：
					
				</view>
				<view class="qiuzhiwei">求内推职位：
					
				</view>
				<view class="yongjin">内推佣金：
					
				</view>
				<view class="miaoshu">描述：
					
				
			</view>
			<view class="kuai">
				
			</view>
			<view class="ziwo">自我介绍
				
			</view>
			<view class="jingyan">项目经验
				
			</view>
			<view class="listDataInternshipExperience">

				{{listData.internshipExperience}} </view>
			<view class="rebut">
				<u-button class="but-o" type="primary" @click="wait(listData)">待选</u-button>
				<button class="but-t" type="primary" @click="next(listData.id)">下一个</button>
				<u-button class="but-s" type="primary" @click="delet(listData.id)">删除</u-button>
				
			</view>
	</view>

</template>

<script>
	export default {
		data() {
			return {
				listData: [],
				a: 0,
				// infoList:[],


			}
		},
		methods: {
			onLoad: function(options) {
				var listData = JSON.parse(options.listData);
				this.listData = listData;
				console.log(listData);
				this.$u.get('http://112.74.58.46:8103/resume/info/selectAllResumeList', {
					recruitId: 1,
					memberId: 59
				}).then(res => {
					console.log(res);
					this.infoList = res;
				});
			},
			delet(index) {
				console.log(index);
				uni.request({
					url: 'http://112.74.58.46:8103/resume/info/deleteResumeById?resumeId=' + index + '&recruitId=1',
					method: 'POST',
					header: {
						'Content-type': 'application/json',
					},
					success: res => {
						console.log(res);
						uni.redirectTo({
							url: '../list/list'
						});
					}
				})
				this.next(index);
				// this.$u.get('member/info/getMemberInfo', {
				// 	username: 'test'
				// }).then(res => {
				// 	["nickname", "username", "id"].forEach((key) => {
				// 		if (key in res) {
				// 			this[key] = res[key]
				// 		}
				// 	});
				// })
			},
			// getInfoList(){
			// 	this.$u.get('http://112.74.58.46:8103/resume/info/selectAllResumeList', {
			// 			recruitId:1,
			// 			memberId:59
			// 		}).then(res => {
			// 			console.log(res);
			// 			this.infoList=res;
			// 	});
			// },

			next(id) {
				// const that = this;
				// let a=this.detailid+1;
				// detailid=detailid+1;

				this.a = this.a + 1;
				console.log(this.a);
				//  this.a=this.a+1;
				// let i =this.a;
				// console.log(this.infoList[detailid]);
				// var listData = JSON.parse(options.listData[a+1]);
				// this.listData=listData;
				// console.log(listData);
				this.listData = this.infoList[this.a];
				console.log(this.listData);
				// console.log(listData)
				// uni.navigateTo();


				// let k=i+1;
				// let pages = getCurrentPages(); //当前页面栈  



				//     let beforePage = pages[pages.length -i]; //获取上一个页面实例对象  
				//      beforePage.$vm.change(detailid-1); //触发父页面中的方法change()  
				//       // beforePage.change(detailid);
				//     // this.$emit("pChangeType");
				// 	// console.log(798);
				// 	// console.log(detailid);
				// 	// uni.navigateTo();
				// 	console.log(this.a);
				// 	console.log(pages)



			},


			wait(index) {

				console.log(index);
				var waitId = index.id;
				uni.request({
					url: 'http://112.74.58.46:8103/resume/info/updateTypeToBeElected?resumeId=' + index.id + '&recruitId=1',
					method: 'POST',
					header: {
						'Content-type': 'application/json',
					},
					success: res => {


					}
				})
				this.next(waitId);
			},
		}
	}
</script>

<style>
	uni-page-body,
	* {
		margin: 0px;
		border: 0px;

	}

	.jianlixiangqing {
		width: 134rpx;
		height: 32rpx;
		font-size: 34rpx;
		font-family: PingFangSC;
		font-weight: 500;
		color: #333333;
		margin-left: 308rpx;
		margin-top: 0px;
		/* margin:0 auto; */
		word-break: keep-all;
		white-space: nowrap;





	}

	.kk {
		width: 750rpx;
		height: 1rpx;
		background: #EEEEEE;
		margin-top: 29rpx;
	}

	.item-img {
		width: 140rpx;
		height: 140rpx;
		background: #00A8FF;
		border-radius: 10rpx;
		margin-left: 30rpx;
		margin-top: 50rpx;
		float: left;

	}

	.listDataName {
		width: 105rpx;
		height: 34rpx;
		font-size: 36rpx;
		font-family: PingFangSC;
		font-weight: 600;
		color: #333333;
		/* margin-left: 119rpx; */
		margin-top: 60rpx;
		margin-right: 446rpx;
		float: right;


	}

	.listDataGraduationSchool {
		width: 166rpx;
		height: 23rpx;
		font-size: 24rpx;
		font-family: PingFang;
		font-weight: 500;
		color: #333333;
		margin-top: 60rpx;
		float: right;
		margin-right: 384rpx;

	}

	.ll {
		width: 549rpx;
		height: 1rpx;
		background: #DDDDDD;
		margin-top: 56rpx;
		float: right;

	}

	.icon1 {
		margin-top: 31rpx;
		margin-left: 203rpx;
		float: left;
	}
	.icn2{
		width: 30rpx;
		height: 26rpx;
		margin-top: 26rpx;
		margin-right: 518rpx;
		float: right;
		

	}
	.qiuneitui{
		width: 491rpx;
		height: 29rpx;
		font-size: 35rpx;
		font-family: PingFang;
		font-weight: 800;
		color: #333333;
		margin-top: 380rpx;
		margin-left: 33rpx;

	}
	.qiugongsi{margin-top: 50rpx;
		width: 491rpx;
height: 29rpx;
font-size: 30rpx;
font-family: PingFang;
font-weight: 800;
color: #333333;
border-top: 50rpx;
float: left;
margin-left: 80rpx;

		
	}
	.qiuzhiwei {margin-top: 50rpx;
		width: 491rpx;
height: 29rpx;
font-size: 30rpx;
font-family: PingFang;
font-weight: 800;
color: #333333;
border-top: 50rpx;
float: left;
margin-left: 80rpx;
		
	}
	.yongjin{margin-top: 50rpx;
		width: 491rpx;
height: 29rpx;
font-size: 30rpx;
font-family: PingFang;
font-weight: 800;
color: #333333;
border-top: 50rpx;
float: left;
margin-left: 80rpx;
		
	}
	.miaoshu{margin-top: 50rpx;
		width: 491rpx;
height: 29rpx;
font-size: 30rpx;
font-family: PingFang;
font-weight: 800;
color: #333333;
border-top: 50rpx;
float: left;
margin-left: 80rpx;
		
	}
	.kuai{
		width: 750rpx;
		height: 20rpx;
		background: #DDDDDD;
		margin-top: 100rpx;
		float: left;

	}
	.ziwo{
		width: 137px;
		height: 34rpx;
		font-size: 35rpx;
		font-family: PingFang;
		font-weight: 800;
		color: #333333;
		margin-top: 30rpx;
		margin-left: 36rpx;
		float: left;
		margin-bottom: 200rpx;

	}
	.jingyan{
		width: 142rpx;
		height: 34rpx;
		font-size: 35rpx;
		font-family: PingFangSC;
		font-weight: 600;
		color: #333333;
		margin: 36rpx;
		margin-bottom: 400rpx;

	}
	

	.listDataInternshipExperience {
		width: 328rpx;
		height: 28rpx;
		font-size: 30rpx;
		font-family: PingFang;
		font-weight: 500;
		color: #333333;
		margin-top: 350rpx;
		float: left;

	}

	.rebut {
		position: absolute;
		margin-top: 600rpx;

	}

	/* .customStyle{
		margin-bottom: 20px;	
		width: 300px;
	} */

	.but-o {
		width: 200rpx;
		height: 90rpx;
		background: #00A8FF;
		border-radius: 5rpx;
		margin-left: 30rpx;
		position: absolute;
		

	}

	.but-t {
		width: 200rpx;
		height: 90rpx;
		background: #00A8FF;
		border-radius: 5rpx;
		float: left;
		margin-left: 260rpx;
		position: absolute;
		

	}

	.but-s {
		width: 200rpx;
		height: 90rpx;
		background: #00A8FF;
		border-radius: 5rpx;
		float: left;
		margin-left: 490rpx;

	}
</style>
