<template>
  <view class="page">
    <view class="content">
      <view class="itemGroup" v-for="(item, index) in items" :key="index">
        <view class="item">
          <image class="itemImage" :src="item.image" />
          <text class="itemTitle">{{ item.title }}</text>
        </view>
      </view>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      items: [
        {
          image: "http://ith2.cn:9000/typora-pic/202411102356981.jpg",
          title: "谜踪之国-楼兰妖耳"
        },
        {
          image: "http://ith2.cn:9000/doc-pic/mzzg-wyzp.jpg",
          title: "谜踪之国-雾隐占婆"
        },
        {
          image: "http://ith2.cn:9000/typora-pic/202411102356981.jpg",
          title: "谜踪之国-楼兰妖耳"
        },
        {
          image: "http://ith2.cn:9000/doc-pic/mzzg-wyzp.jpg",
          title: "谜踪之国-雾隐占婆"
        },
        {
          image: "http://ith2.cn:9000/doc-pic/mzzg-wyzp.jpg",
          title: "谜踪之国-雾隐占婆"
        },
        {
          image: "http://ith2.cn:9000/typora-pic/202411102356981.jpg",
          title: "谜踪之国-楼兰妖耳"
        },
        {
          image: "http://ith2.cn:9000/doc-pic/mzzg-wyzp.jpg",
          title: "谜踪之国-雾隐占婆"
        },
        {
          image: "http://ith2.cn:9000/doc-pic/mzzg-wyzp.jpg",
          title: "谜踪之国-雾隐占婆"
        },
        {
          image: "http://ith2.cn:9000/typora-pic/202411102356981.jpg",
          title: "谜踪之国-楼兰妖耳"
        },
        {
          image: "http://ith2.cn:9000/doc-pic/mzzg-wyzp.jpg",
          title: "谜踪之国-雾隐占婆"
        },
        {
          image: "http://ith2.cn:9000/doc-pic/mzzg-wyzp.jpg",
          title: "谜踪之国-雾隐占婆"
        },
        {
          image: "http://ith2.cn:9000/typora-pic/202411102356981.jpg",
          title: "谜踪之国-楼兰妖耳"
        },
        {
          image: "http://ith2.cn:9000/doc-pic/mzzg-wyzp.jpg",
          title: "谜踪之国-雾隐占婆"
        }
      ]
    };
  },
  onLoad() {
    console.log("组件加载");
  },
  methods: {}
};
</script>

<style>
/* 页面根容器 */
.page {
  width: 100%;
  height: 100vh;
  display: flex;
  flex-direction: column;
  overflow: hidden; /* 禁止外部滚动 */
  //background-color: rgb(34, 34, 34);
  background-color: rgba(255, 255, 255, 0.83);
}

/* 内容区域允许滚动 */
.content {
  flex: 1;
  display: flex;
  flex-wrap: wrap; /* 允许换行 */
  justify-content: space-between; /* 两列之间有间隔 */
  overflow-y: auto; /* 向上滑动时只滚动内容 */
  padding: 20rpx;
}

.itemGroup {
  margin-top: 20rpx;
  margin-bottom: 20rpx;
  width: 48%; /* 每个项占屏幕宽度的48% */
  height: 350rpx;
}

.item {
  position: relative;
  width: 100%; /* 宽度 100% */
  padding-top: 110%; /* 设置padding-top为100%，使图片保持正方形 */
  border-radius: 10rpx; /* 圆角效果 */
  overflow: hidden;
}

.itemImage {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 90%;
  object-fit: cover;
}

.itemTitle {
  position: absolute;
  bottom: -2rpx; /* 标题距离底部的距离 */
  left: 15%;
  //color: white;
  color: #222222;
  font-size: 23rpx;
  font-family: PingFangSC-Medium;
}
</style>
