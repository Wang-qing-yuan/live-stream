<template>
  <view>
    <image src="../../static/banner/1.jpg" style="width: 750rpx; height: 250rpx;"></image>
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
      <f-list
        class="list-item"
        v-for="(item, index) in list"
        :key="index"
        :item="item"
        :index="index"
        @click="openLive"
      ></f-list>
    </view>
    
  </view>
</template>

<script>
import fList from '@/components/common/f-list.vue';
export default {
  components: {
    fList
  },
  data() {
    return {
      list: [
        {
          name: '迷人景色',
          img: '../../static/list-1.jpg',
          money: 100,
          popular: 10,
          status: 0
        },
        {
          name: '摄像',
          img: '../../static/list-2.jpg',
          money: 30,
          popular: 8,
          status: 1
        },
        {
          name: '宿舍毕业照',
          img: '../../static/list-3.jpg',
          money: 50,
          popular: 1,
          status: 0
        },
        {
          name: '我在南京学摄影',
          img: '../../static/list-4.jpg',
          money: 60,
          popular: 1,
          status: 0
        },
        {
          name: '交换空间',
          img: '../../static/list-5.jpg',
          money: 70,
          popular: 1,
          status: 1
        },
		{
		  name: '画小画',
		  img: '../../static/list-6.jpg',
		  money: 70,
		  popular: 1,
		  status: 1
		},
		{
		  name: '高楼远眺',
		  img: '../../static/list-7.jpg',
		  money: 70,
		  popular: 1,
		  status: 1
		},
		{
		  name: '旅途',
		  img: '../../static/list-8.jpg',
		  money: 70,
		  popular: 1,
		  status: 1
		},
      ]
    };
  },
  onLoad() {},
  methods: {
    openLive() {
      uni.navigateTo({
        url: '../live/live'
      });
    }
  }
};
</script>

<style>
.list-item {
  width: 375rpx;
  height: 375rpx;
  padding: 5rpx;
  box-sizing: border-box;
  position: relative;
}
</style>