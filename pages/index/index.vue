<template>
	<view>
		<!-- <image src="../../static/banner/3.jpg" style="width: 750rpx; height: 250rpx;"></image> -->
		<view class="top flex align-center justify-center">
			<input
				style="width: 600rpx;height: 70rpx; background-color: rgba(0,0,0,0.2);"
				type="text"
				class="rounded-circle mx-1 pl-5"
				placeholder="搜索直播间"
			/>
		</view>
		<!-- 轮播图 -->
		<!-- <swiper
      :indicator-dots="true"
      :autoplay="true"
      :interval="3000"
      :duration="200"
      style="width: 750rpx; height: 250rpx;"
    >
      <swiper-item>
        <image src="../../static/banner/1.jpg" style="width: 750rpx; height: 250rpx;"></image>
      </swiper-item>
      <swiper-item>
        <image src="../../static/banner/2.jpg" style="width: 750rpx; height: 250rpx;"></image>
      </swiper-item>
    </swiper> -->

		<!-- 列表 -->
		<view class="flex flex-wrap">
			<view class="list-item" v-for="(item, index) in list" :key="index">
				<f-card :item="item" :index="index" @click="openLive(item.id)"></f-card>
			</view>
		</view>

		<view class="f-divider"></view>
		<view class="flex align-center justify-center py-3">
			<text class="font-md text-secondary">{{ loadText }}</text>
		</view>
	</view>
</template>

<script>
import fCard from '@/components/common/f-card.vue';
export default {
	components: {
		fCard
	},
	data() {
		return {
			list: [],
			page: 1,
			loadText: '上拉加载更多'
		};
	},
	onLoad() {
		this.getData();
	},
	onPullDownRefresh() {
		this.page = 1;
		this.getData()
			.then(res => {
				uni.showToast({
					title: '刷新成功',
					icon: 'none'
				});
				uni.stopPullDownRefresh();
			})
			.catch(err => {
				uni.stopPullDownRefresh();
			});
	},
	onReachBottom() {
		if (this.loadText != '上拉加载更多') {
			return;
		}
		this.loadText = '加载中...';
		this.page++;
		this.getData();
	},
	methods: {
		getData() {
			let page = this.page;
			return this.$H
				.get('/live/list/' + page)
				.then(res => {
					(this.list = page === 1 ? res : [...this.list, ...res]),
						(this.loadText = res.length < 10 ? '没有更多了' : '上拉加载更多');
				})
				.catch(err => {
					if (this.page > 1) {
						this.page--;
						this.loadText = '上拉加载更多';
					}
				});
		},
		openLive(e) {
			console.log(e);
			uni.navigateTo({
				url: '../live/live?id=' + e
			});
		}
	}
};
</script>

<style>
.top {
	width: 750rpx;
	height: 260rpx;
	background-image: url(../../static/banner/3.jpg);
	background-size: cover;
	background-image: linear-gradient(to right, #ba7ace 0%, #8745ff 100%);
}
.list-item {
	width: 375rpx;
	height: 375rpx;
	padding: 5rpx;
	box-sizing: border-box;
	position: relative;
}
</style>
