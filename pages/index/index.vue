<template>
	<view class="background">
		<view class="hello">
			<view class="title">欢迎你：{{ user.username }}</view>
			<view class="title">当前待取餐：</view>
		</view>
		<view class="todo">
			<view class="content">
				<view class="order">订单编号：{{ user.todo.oid }}</view>
				<view class="telephone">手机号：{{ user.todo.telephone }}</view>
				<view class="state">当前状态：{{ user.todo.state }}</view>
			</view>
		</view>
		<view class="qrBg" @click="toScan">
			<view class="qrIcon">
				<image src="../../assets/scan_icon.png" class="img" />
				<view class="text">请点击此处扫描二维码</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			let state = uni.getStorageSync('state')
			if (!state) {
				uni.setStorageSync('state', '待取餐');
				state = '待取餐'
			}
			return {
				result: '',
				error: '',
				user: {
					username: '王先生',
					todo: {
						oid: '1487123172',
						telephone: '156****7452',
						state,
					},
				},
			}
		},
		methods: {
			toScan() {
				let that = uni
				uni.scanCode({
					onlyFromCamera: true,
					success: function(res) {
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
						that.navigateTo({
							url: '../user/besure/besure?id=123456'
						});
						console.log(res.result)
					},
				});
			},
		}
	}
</script>

<style lang="scss">
	.background {
		padding: 40rpx 40rpx 0 40rpx
	}

	.hello {
		padding: 30rpx 40rpx
	}

	.todo {
		padding: 30rpx 0;
	}

	.content {
		padding: 30rpx 40rpx;
		background-color: rgba($color: #ffffff, $alpha: .3);
		border-radius: 30rpx;
	}

	.img {
		width: 300rpx;
		height: 300rpx;
	}

	.qrBg {
		padding-top: 30rpx;
		text-align: center;
	}
</style>
