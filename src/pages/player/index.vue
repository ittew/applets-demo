<template>
  <div class="wrapper">
    <div class="header">
      <div class="title">第一集：田忌赛马</div>
      <div class="views-box">
        <img src="http://imagev2.xmcdn.com/group59/M01/AC/BB/wKgLel0_rnmAmP1hAAgVnsU0jxA823.jpg" alt="">
        <div class="views">194.6万</div>
      </div>
      <div class="slider-box">
        <slider @change="sliderChange" :value="myAudioPos" block-size='10' block-color='#e97b6a' backgroundColor="#d8d8d8" activeColor="#e97b6a"
        />
        <div class="time">
          <div class="current-time">{{myAudioCurrent}}</div>
          <div class="duration-time">{{myAudioDuration}}</div>
        </div>
      </div>
    </div>
    <div class="player-box">
      <div class="controls">
        <img class="prev" src="/static/player/prev.png" alt="">
        <img class="play" @tap="playHandle" v-show="!isPlay" src="/static/player/pause.png" alt="">
        <img class="pause" @tap="pauseHandle" v-show="isPlay" src="/static/player/play.png" alt="">
        <img class="next" src="/static/player/next.png" alt="">
      </div>
    </div>
    <div class="view-info">
      <div class="item">
        <img src="" alt=""><span>播放列表</span>
      </div>
      <div class="item">
        <img src="" alt=""><span>373</span>
      </div>
      <div class="item">
        <img src="" alt=""><span>1.1万</span>
      </div>
      <div class="collection-box">
        <img src="http://imagev2.xmcdn.com/group59/M01/AC/BB/wKgLel0_rnmAmP1hAAgVnsU0jxA823.jpg" alt="">
        <div class="title-number">
          <div class="title">米小圈动画成语课</div>
          <div class="number">7.5万人收藏</div>
        </div>
        <div class="collection">
          <span></span>
          <span>收藏</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      isPlay: false, // 是否播放
      myAudioCurrent: '0', // 音频当前已播放时间
      myAudioDuration: '0', // 音频总时长
      myAudio: '', // 音频实例
      myAudioPos: 0 // 当前滑块的位置
    }
  },

  components: {
  },

  methods: {
    // 滑块滑动完成事件
    sliderChange (e) {
      // 当前slider滑动的距离
      const position = e.target.value
      // 根据滑动位置计算出当前所对应的时间
      let currentTime = position / 100 * this.myAudio.duration
      // 跳转到指定位置 单位s秒
      console.log(currentTime, 'currentTime')
      this.myAudio.seek(currentTime)
      console.log(this.myAudio.currentTime, 'this.myAudio.currentTime')
      // 传入空函数暂时不执行实时监听播放进度更新事件 防止和slider滑动位置出现跳动问题
      // this.myAudio.onTimeUpdate(function(){})
      // 更新当前已播放时间
      // this.myAudioCurrent = this.format(currentTime)
      this.updateTime()
    },
    // 播放
    playHandle () {
      // 考虑到进度条被拖动，不一定从00:00:00开始 当前开始播放的时间
      this.myAudio.startTime = this.myAudioCurrent
      // 播放
      this.myAudio.play()
      this.isPlay = true
      this.updateTime()
    },
    updateTime () {
      // 进度条变化
      this.myAudio.onTimeUpdate(() => {
        // 更新滑块位置
        this.myAudioPos = this.myAudio.currentTime / this.myAudio.duration * 100
        // 更新当前已播放时间
        this.myAudioCurrent = this.format(this.myAudio.currentTime)
      })
    },
    // 暂停
    pauseHandle () {
      this.myAudio.pause()
      this.isPlay = false
    },
    // 时间格式化
    format (t) {
      let time = Math.floor(t / 60) >= 10 ? Math.floor(t / 60) : '0' + Math.floor(t / 60)
      t = time + ':' + ((t % 60) / 100).toFixed(2).slice(-2)
      return t
    }
  },

  created () {
    this.myAudio = wx.createInnerAudioContext()
    this.myAudio.src = 'http://ws.stream.qqmusic.qq.com/C400001xLIXo2w9V7U.m4a?guid=7202258340&vkey=2203B4A0922854C0F9CE18933C0D8C452F9A026CF9166463AF7443918543AAC6F902DD9165F6D72168D5538140AD294D53525519B0B702CF&uin=7347&fromtag=66'
    this.myAudio.title = 'Cannon'
    console.log(this.myAudio)
    // 在onCanplay里获取并设置音频时长和播放进度
    this.myAudio.onCanplay(() => {
      // eslint-disable-next-line
      this.myAudio.duration // 必须写，不然获取不到。。。
      setTimeout(() => {
        this.myAudioDuration = this.format(this.myAudio.duration) // 总时长
        this.myAudioCurrent = this.format(this.myAudio.currentTime) // 当前已播放时间
      }, 1000)
    })

    // 播放完成处理，按钮变一下
    this.myAudio.onEnded((res) => {
      this.myAudioPos = 0
      this.isPlay = false
    })
  }
}
</script>

<style scoped lang='scss'>
.wrapper{
  .header{
    background: #f4f4f4;
  }
  .title{
    font-size: 40rpx;
    font-weight: bold;
    text-align: center;
    padding: 56rpx 0;
  }
  .views-box{
    border-radius: 10rpx;
    width: 360rpx;
    height: 360rpx;
    overflow: hidden;
    margin: 0 auto;
    position: relative;
    img{
      width: 100%;
      height: 100%;
    }
    .views{
      position: absolute;
      bottom: 0;
      width: 100%;
      font-size: 24rpx;
      text-align: right;
      padding-right: 10rpx;
      line-height: 50rpx;
      height: 50rpx;
      color: #fff;
      background: rgba(0,0,0,.1);
      box-sizing: border-box;
    }
  }
  .player-box{
    margin-top: 60px;
    .controls{
      height: 90rpx;
      display: flex;
      justify-content: space-between;
      padding:0 175rpx;
      align-items: center;
    }
    .next,.prev{
      width: 50rpx;
      height: 45rpx;
    }
    .play, .pause{
      width: 75rpx;
      height: 86rpx;
    }
  }
  .slider-box{
    padding-bottom: 40rpx;
    .time{
      display: flex;
      justify-content: space-between;
      padding: 0 36rpx;
      font-size: 28rpx;
    }
  }
}
</style>
