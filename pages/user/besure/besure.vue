<template>
	<view class="background">
		<view class="container">
			<view class="texts">
				<view class="title">您的外卖当前所在柜门号为：</view>
				<view class="title" style="font-size: 30px">{{id}}</view>
				<view class="title">是否开箱？</view>
			</view>
			<view class="buttons">
				<u-button class="button" type="primary" size="medium" plain ripple @click="sure">确认</u-button>
			</view>
			<view class="buttons">
				<u-button class="button" type="primary" size="medium" plain ripple @click="cancel">取消</u-button>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		onLoad(option) {
			this.id = option.id
		},
		data() {
			return {
				id: '',
			};
		},
		methods: {
			sure() {
				console.log("确认")
				uni.request({
					url: 'https://www.fastmock.site/mock/ff907d7ca812655e3b9650cdca54ba48/tusake/classify',
					method: 'GET',
					timeout: 3000,
					dataType: 'json',
					success(res) {
						console.log(res.data.code)
					},
					fail(e) {
						console.log(e)
					}
				})
				uni.redirectTo({
					url: '../result/result'
				});
			},
			cancel() {
				console.log("取消")
				uni.switchTab({
					url: '/pages/index/index'
				});
			}
		},
	}
</script>

<style>
	.container {
		padding-top: 25vh;
	}

	.texts {
		padding-bottom: 5vh;
	}

	.title {
		text-align: center;
	}

	.buttons {
		padding: 1vh 0;
		display: flex;
		align-items: center;
	}

	.button {
		width: 40vw;
		font-size: 30rpx;
	}
</style>
