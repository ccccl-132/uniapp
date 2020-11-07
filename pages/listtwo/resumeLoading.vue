<template>
	<view class="container">
		<view class="liebiao">
			<ul class="tab">
				<li>全部</li>
				<li>待选({{daixuan}})</li>
				<li @click="resumeLoading()">面试中({{mianshizhong}})</li>
				<li>通过({{pass}})</li>
				<li>失败({{shibai}})</li>
			</ul>
		</view>
		<view class="jianli" v-for="(item, index) in listDatatwo" :key="index">
			<view class="jianli-left">
				<image src="" mode=""></image>
			</view>
			<view class="jianli-right">
				<view class="tex">姓名：{{item.name}}</view>
				<view class="tex">学校：{{item.graduationSchool}}</view>
				<view class="tex">实习经历：{{item.internshipExperience}}</view>
				<button type="default" @click="hahah()">通过</button>
				<view class="passbut">
					<view class="">面试/(</view>
					<view class="" @click="win()">通过/</view>
					<view class="" @click="lost()">失败)</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				daixuan:'0',
				mianshizhong:'0',
				pass:'0',
				shibai:'0',
				name:'',
				graduationSchool:'',
				internshipExperience:'',
				listDatatwo:[],
				id:'',
				memberId:59,
				recruitld:1,
			}
		},
		methods: {
			// onLoad: function (options) {
			//     var listDataname = JSON.parse(options.listDataname);
			// 	// this.listDatatwo.push(listDataname);
			// 	this.listDatatwo[this.listDatatwo.length]=listDataname;
			// 	console.log(listDataname);
			// 	this.daixuan=this.listDatatwo.length;
			// },
			hahah(){
				console.log(this.listDatatwo);
				// uni.redirectTo({
				//     url: '../list/list'
				// });
			},
			// win(){
			// 	this.pass++;
			// },
			// lost(){
			// 	this.shibai=this.shibai + 1;
			// }
			resumeLoading(){
				this.$u.route({
					url: 'pages/listtwo/resumeLoading',
				})
			}
		}
	}
</script>

<style>
	.liebiao{
		overflow: hidden;
	}
	.tab li{
		list-style: none;
		float: left;
		margin-right: 5px;
	}
	.jianli{
		background-color: #E5E5E5;
		height: 200px;
	}
	.jianli-left{
		height: 200px;
		width: 120px;
		/* background-color: #007AFF; */
		float: left;
	}
	.jianli-right{
		height: 200px;
		width: 255px;
		/* background-color: #4CD964; */
		float: left;
	}
	.tex{
		margin-bottom: 10px;
	}
	.passbut{
		width: 150px;
		background-color: #00A8FF;
	}
	.passbut view{
		display: inline;
	}
</style>