<template>
	<view class="content">
		<button type="default" @click="goto('../login/login')">登陆</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				news : []
			};
		},
		onLoad:function(){
		},
		methods: {
			goto(url) {
				uni.navigateTo({
					url:url
				})
			}
		},
	}
</script>

<style>
	.content{
		margin-top: 50px;
	}
</style>
