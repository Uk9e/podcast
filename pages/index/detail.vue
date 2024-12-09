<template>
<view class="root">
  <view class="container">
    <image :src="coverImgUrl" class="cover"></image>

    <!-- 进度条 -->
    <view class="progress-bar">
      <slider
          :value="progressValue"
          block-size="20"
          @changing="seekAudio"
      />
      <view class="time-container">
        <text>{{ formatTime(currentTime) }}</text>
        <text>{{ formatTime(duration) }}</text>
      </view>
    </view>

    <!-- 控制按钮 -->
    <view class="controls">
      <button>
        {{ '⏪️' }}
      </button>
      <button @click="isPlaying ? pauseAudio() : playAudio()">
        {{ isPlaying ? '⏸️' : '▶️' }}
      </button>
      <button>
        {{ '⏩️' }}
      </button>
    </view>
  </view>
</view>
</template>

<script>
export default {
  data() {
    return {
      audioSrc: 'https://file.ith2.cn/mzzg-sntj/1.mp3', // 替换为你的音频URL
      currentTime: 0,
      duration: 0,
      isPlaying: false,
      coverImgUrl: 'https://oss.ith2.cn/doc-pic/202411102356981.jpg',
      progressValue: 0,
    };
  },
  onLoad() {
    this.audioCtx = uni.createInnerAudioContext();
    this.audioCtx.src = this.audioSrc;
    this.audioCtx.onCanplay(() => {
      this.duration = this.audioCtx.duration;
    });
    this.audioCtx.onTimeUpdate(() => {
      this.currentTime = this.audioCtx.currentTime;
      this.progressValue = (this.currentTime / this.duration) * 100;
    });
  },
  onUnload() {
    this.audioCtx.destroy();
  },
  methods: {
    playAudio() {
      if (!this.isPlaying) {
        this.audioCtx.play();
        this.isPlaying = true;
      }
    },
    pauseAudio() {
      if (this.isPlaying) {
        this.audioCtx.pause();
        this.isPlaying = false;
      }
    },
    seekAudio(value) {
      const timeToSeek = (value / 100) * this.duration;
      this.audioCtx.seek(timeToSeek);
      this.currentTime = timeToSeek;
      this.progressValue = value;
    },
    formatTime(time) {
      const minutes = Math.floor(time / 60);
      const seconds = Math.floor(time % 60).toString().padStart(2, '0');
      return `${minutes}:${seconds}`;
    }
  }
};
</script>

<style>
/* 添加一些样式 */
.container {
  height: 90vh;
  margin-top: 80rpx;
  padding: 50rpx;
}

.cover {
  position: relative;
  width: 100%; /* 宽度 100% */
  height: 700rpx;
  border-radius: 10rpx; /* 圆角效果 */
  overflow: hidden;
}

.controls {
  display: flex;
  justify-content: space-around; /* 按钮之间均匀分布 */
  width: 100%; /* 根据需要调整宽度 */
  margin-top: 50rpx;
}

.controls button {
  background: none;
  border: none;
  font-size: 30rpx; /* 调整图标大小 */
  cursor: pointer;
}

.controls button:hover {
  opacity: 0.7; /* 鼠标悬停时稍微变暗 */
}


.progress-bar {
  width: 100%; /* 根据需要调整宽度 */
  margin-top: 20px;
  position: relative; /* 用于定位 time-container */
}

.time-container {
  display: flex;
  justify-content: space-between;
  position: absolute;
  width: 100%;
  font-size: 20rpx; /* 根据需要调整字体大小 */
}

.time-container text {
  white-space: nowrap;
}

</style>
