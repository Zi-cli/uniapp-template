<template>
	<view class="content">
		<image class="logo" src="/static/logo.png"></image>
		<view class="text-area">
			<text class="title">{{title}}</text>
		</view>
		<u-icon name="photo"></u-icon>
		<u-button>月落</u-button>
		<test-rate></test-rate>
		<x-one></x-one>
		<x-two></x-two>
		<navigator url="/pages/subpages/acount/acount" open-type="navigate">去分包页</navigator>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {
			// 调用getSearch接口
			this.$u.api.getSearch().then(res => {
				console.log(res);
			}).catch(err => {
				
			})
			
			// 调用getInfo接口
			this.$u.api.getInfo({id: 3}).then(res => {
				console.log(res);
			}).catch(err => {
				
			})
		},
		methods: {

		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
