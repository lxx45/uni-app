<script>
	export default {
		onLaunch: function() {
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

<style>
	/*每个页面公共css */
	/* 引人官方css */
	@import './common/uni.css';
	/* 引人自定义图标库 */
	@import './common/icon.css';
	/* 引人动画库 */
	@import './common/animate.css';
	/* 公共样式 */
	@import './common/common.css';
</style>
