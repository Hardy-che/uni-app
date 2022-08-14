<template>
	<view class="container">
		<uni-nav-bar @clickRight="goto('../create/create')" fixed="true">
			<view class="input-view">
				<uni-icons class="input-uni-icon" type="search" size="18" color="#999"></uni-icons>
				<input confirm-type="search" v-model= "searchValue" class="uni-bar-input" type="text" placeholder="搜索帖子" @confirm="search">
			</view>
			<block slot="right"><view class="iconfont icon-bianjiqianbi"></view></block>
		</uni-nav-bar>
		<!-- <view>{{searchValue}}</view>s -->
		<view class="main-body">
			<scroll-view class="scrollview" scroll-y="true">
				<view id="demo1" class="scrollitem">111</view>
				<view id="demo2" class="scrollitem">222</view>
				<view id="demo3" class="scrollitem">333</view>
				<view id="demo4" class="scrollitem">444</view>
			</scroll-view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				searchValue: ''
			};
		},
		
		methods: {
			search(res) {
				console.log(res);
				console.log(res.detail.value);
				uni.navigateTo({
					url:'../search/search'
				});
			},
			
			goto(url) {
				uni.navigateTo({
					url: '../create/create'
				});
			}
		},
		
		onReachBottom() {
			console.log('已经到达底部');
		}
	}

</script>

<style>
	.input-view{
		display: flex;
		height: 60rpx;
		width: 500rpx;
		background-color: #f8f8f8;
		border-radius: 15px;
		padding: 0 15px;
		flex-wrap: nowrap;
		margin: 7px 0;
	}
	
	.input-uni-icon{
		line-height: 60rpx;
	}
	
	.uni-bar-input{
		height: 60rpx;
		width: 400rpx;
		line-height: 60rpx;
		padding-left: 15rpx;
		font-size: 20rpx;
	}
	
	.scrollview{
		height: 100%;
	}
	
	.scrollitem{
		height: 300rpx;
	}
</style>