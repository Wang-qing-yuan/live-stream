<script>
export default {
	onLaunch: function() {
		console.log('App Launch');
		this.$store.dispatch('connectSocket');
		const domModule = weex.requireModule('dom');
		domModule.addRule('fontFace', {
			fontFamily: 'iconfont',
			src: "url('http://at.alicdn.com/t/font_1859985_7mxozsfdvib.ttf')"
		});

		//监听底部导航中间凸起按钮
		uni.onTabBarMidButtonTap(() => {
			this.authJump({
				url: '/pages/create-live/create-live'
			});
			console.log('点击了中间按钮');
		});
		this.$store.dispatch('initUser');
	},
	onShow: function() {
		console.log('App Show');
	},
	onHide: function() {
		console.log('App Hide');
	}
};
</script>

<style>
/*引入公共样式库 */
@import url('./common/common.css');
/*引入free样式库 */
@import url('./common/free.css');
/*引入图标库 */
/* #ifndef APP-PLUS-NVUE */
@import url('./common/icon.css');
/* #endif */
</style>
