<template>
	<view class="container">
		<view class="iconfont icon-fork" @click="goto('../index/index')"></view>
		
		<form v-if="logWay == '手机验证码登陆'" class="loginform">
			<view class="title">手机验证码登陆</view>
			<view class="form-col">
				<text>+86</text>
				<input type="number" placeholder="手机号" />
			</view>
			<view class="form-col">
				<input type="number" placeholder="请输入验证码" />
				<button class="getCodeBtn" type="primary" @click="getCode">{{!countCode? '获取验证码':countCode + 's'}}</button>
			</view>
			<button class="loginBtn" @click="goto('../home/home')">登陆</button>
			<view class="changeLog">
				<text @click="changeLogWay" style="color: darkturquoise;">账号密码登陆</text>
				<text>|</text>
				<text style="color: darkturquoise;"> 登陆遇到问题 </text>
			</view>
		</form>
		
		<form v-if="logWay == '账号密码登陆'" class="loginform">
			<view class="title">账号密码登陆</view>
			<view class="form-col">
				<input placeholder="昵称/手机号/邮箱" />
			</view>
			<view class="form-col">
				<input type="password" placeholder="请输入密码" />
				<text class="forgetPwd">忘记密码</text>
			</view>
			<button class="loginBtn" @click="goto('../home/home')">登陆</button>
			<view class="changeLog">
				<text @click="changeLogWay" style="color: darkturquoise;">手机验证码登陆</text>
				<text>|</text>
				<text style="color: darkturquoise;"> 登陆遇到问题 </text>
			</view>
		</form>
		
		<text class="loginText">------社交账号登陆------</text>
		<view class="socialPlatform">
			<view class="iconfont icon-QQ"></view>
			<view class="iconfont icon-weixin"></view>
			<view class="iconfont icon-weibo"></view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				logWay: '手机验证码登陆',
				countCode: 0
			}
		},
		methods:{
			changeLogWay(){
				if(this.logWay == '手机验证码登陆'){
					this.logWay = '账号密码登陆'
				}else if(this.logWay == '账号密码登陆'){
					this.logWay = '手机验证码登陆'
				}
			},
			
			getCode(){
				if(this.countCode>0){
					uni.showToast({
						title:'不能重复获取',
						icon: "none"
					})
				}else{
						this.countCode = 60
						let timer = setInterval(() => {
							this.countCode--;
							if (this.countCode<1){
								clearInterval(timer);
								this.countCode=0;
							}
							}, 1000)
					}
			},
			
			goto(url) {
				uni.switchTab({
					url:url
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.container{
		width: 100vw;
		height: 100vh;
		display: flex;
		flex-direction: column;
	}
	
	.title{
		font-size: 25px;
		text-align: center;
		margin-top: 50px;
	}
	
	.loginform{
		margin-top: 50px;
		padding: 0 50upx;
	}
	
	.form-col{
		display: flex;
		border-bottom: 1rpx solid #545454;
		margin: 20px 30px;
		align-items: flex-end;
	}
	
	.getCodeBtn{
		margin: 0 0;
		height: 100%;
		width: 350rpx;
	}
	
	.changeLog{
		text-align: center;
		margin: 20px 0;
	}
	
	.loginBtn{
		border-radius: 50upx;
		background-color: cornflowerblue;
		margin: 15rpx 30rpx;
	}
	
	.loginText{
		text-align: center;
	}
	
	.socialPlatform{
		
		display: flex;
		justify-content: center;
		margin: 20px 0;
	}
</style>
