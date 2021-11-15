<script>
	export default {
		onLaunch: function() {
			uni.removeStorageSync('state')
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style lang="scss">
	@import "uview-ui/index.scss";

	/*每个页面公共css */
	* {
		font-size: 16px;
	}

	body {
		// background-image: url('./assets/background.jpg');
		background-color: rgba($color: #eee, $alpha: 1.0);
		background-repeat: no-repeat;
		background-size: 100% 100%;
	}

	.title {
		font-size: 40rpx;
	}
</style>
