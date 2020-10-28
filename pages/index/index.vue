<template>
	<view class="content">
		<tab></tab>
	</view>
</template>

<script>
	import tab from '../../components/tab.vue'
	export default {
		data() {
			return {
			}
		},
		components:{
			tab
		},
		onLoad() {
			uni.hideTabBar();
		},
		methods: {

		}
	}
</script>

<style>
	.content {
		width: 100%;
		height: 100%;
		background: #5a5b5a;
	}
</style>
