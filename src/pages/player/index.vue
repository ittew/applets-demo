<template>
  <div class="wrapper">
    <div class="header">
      <div class="title">第一集：田忌赛马</div>
      <div class="views-box">
        <img src="http://imagev2.xmcdn.com/group59/M01/AC/BB/wKgLel0_rnmAmP1hAAgVnsU0jxA823.jpg" alt="">
        <div class="views">194.6万</div>
      </div>
      <div class="slider-box">
        <slider @touchstart="startHandle" @change="sliderChange" :value="myAudioPos" block-size='10' block-color='#e97b6a' backgroundColor="#d8d8d8" activeColor="#e97b6a"
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
      <div class="like-box">
        <div class="item">
          <img src="http://imagev2.xmcdn.com/group59/M01/AC/BB/wKgLel0_rnmAmP1hAAgVnsU0jxA823.jpg" alt=""><span>播放列表</span>
        </div>
        <div class="item">
          <img src="http://imagev2.xmcdn.com/group59/M01/AC/BB/wKgLel0_rnmAmP1hAAgVnsU0jxA823.jpg" alt=""><span>373</span>
        </div>
        <div class="item">
          <img src="http://imagev2.xmcdn.com/group59/M01/AC/BB/wKgLel0_rnmAmP1hAAgVnsU0jxA823.jpg" alt=""><span>1.1万</span>
        </div>
      </div>
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
    <div class="comment-box">
      <div class="all">
        <div class="title">
          <span>全部评论</span>
          <span>(177)</span>
        </div>
        <div class="btn">写评论</div>
      </div>
      <div class="comment-list">
        <div class="item">
          <div class="infor">
            <img src="http://imagev2.xmcdn.com/group59/M01/AC/BB/wKgLel0_rnmAmP1hAAgVnsU0jxA823.jpg" alt="">
            <div class="name-time">
              <div class="name">宝宝巴士</div>
              <div class="time">2020-4-22</div>
            </div>
            <div class="zan-box">
              <div class="zan">5</div>
              <img src="http://imagev2.xmcdn.com/group59/M01/AC/BB/wKgLel0_rnmAmP1hAAgVnsU0jxA823.jpg" alt="">
            </div>
          </div>
          <div class="content">第一个评论</div>
          <div class="replay"></div>
        </div>
        <div class="item">
          <div class="infor">
            <img src="http://imagev2.xmcdn.com/group59/M01/AC/BB/wKgLel0_rnmAmP1hAAgVnsU0jxA823.jpg" alt="">
            <div class="name-time">
              <div class="name">宝宝巴士</div>
              <div class="time">2020-4-22</div>
            </div>
            <div class="zan-box">
              <div class="zan">5</div>
              <img src="http://imagev2.xmcdn.com/group59/M01/AC/BB/wKgLel0_rnmAmP1hAAgVnsU0jxA823.jpg" alt="">
            </div>
          </div>
          <div class="content">第一个评论</div>
          <div class="replay"></div>
        </div>
        <div class="item">
          <div class="infor">
            <img src="http://imagev2.xmcdn.com/group59/M01/AC/BB/wKgLel0_rnmAmP1hAAgVnsU0jxA823.jpg" alt="">
            <div class="name-time">
              <div class="name">宝宝巴士</div>
              <div class="time">2020-4-22</div>
            </div>
            <div class="zan-box">
              <div class="zan">5</div>
              <img src="http://imagev2.xmcdn.com/group59/M01/AC/BB/wKgLel0_rnmAmP1hAAgVnsU0jxA823.jpg" alt="">
            </div>
          </div>
          <div class="content">第一个评论</div>
          <div class="replay"></div>
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
    startHandle () {
      console.log('startHandle')
      this.myAudio.offTimeUpdate() // 取消事件 防止和slider滑动位置出现跳动问题
    },
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
    this.myAudio.src = 'https://eo-sycdn.kuwo.cn/6ef967ef39d8340a1eafc169b6a1e922/5ea3e27b/resource/n2/56/34/1683736193.mp3'
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
      this.myAudioCurrent = '00:00'
      this.isPlay = false
    })
  }
}
</script>

<style scoped lang='scss'>
.wrapper{
  background: #f4f4f4;
  .header{
    .title{
      font-size: 40rpx;
      font-weight: bold;
      text-align: center;
      padding: 56rpx 0;
    }
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
    background: #fff;
    padding-top: 80rpx;
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
  .like-box{
    display: flex;
    justify-content: center;
    padding: 60rpx 0 80rpx;
    .item{
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      margin: 0 40rpx;
      font-size: 28rpx;
      color: #bbb;
      img{
        width: 75rpx;
        height: 60rpx;
        margin-bottom: 20rpx;
      }
    }
  }
  .collection-box{
    margin: 12rpx 0;
    padding: 0 20rpx;
    height: 160rpx;
    background: #fff;
    display: flex;
    align-items: center;
    img{
      width: 120rpx;
      height: 120rpx;
      margin-right: 30rpx;
    }
    .title-number{
      display: flex;
      flex-direction: column;
      .title{
        font-size: 36rpx;
        color: #333;
      }
      .number{
        font-size: 30rpx;
        margin-top: 20rpx;
        color: #999;
      }
    }
    .collection{
      margin-left: auto;
      width: 180rpx;
      color: #f86342;
      font-size: 36rpx;
      line-height: 72rpx;
      text-align: center;
      background: #ffece8;
      border-radius: 42rpx;
    }
  }
  .comment-box{
    background: #fff;
    padding: 40rpx 20rpx;
    .all{
      display: flex;
      justify-content: space-between;
      align-items: center;
      .title{
        font-weight: bold;
        font-size:30rpx;
      }
    }
    .btn{
      border: 1px solid orangered;
      color: orangered;
      border-radius: 50rpx;
      line-height: 50rpx;
      font-size: 28rpx;
      padding: 0 20rpx;
    }
  }
  .comment-list{
    margin-top: 30rpx;
    .item{
      margin-bottom: 30rpx;
      .infor{
        display: flex;
        align-items: center;
        img{
          width: 60rpx;
          height: 60rpx;
        }
        .zan-box{
          margin-left: auto;
          display: flex;
          align-items: center;
          font-size: 24rpx;
          color: #999;
          .zan{
            margin-right: 10rpx;
          }
        }
        .name-time{
          margin-left: 20rpx;
          .name{
            font-size: 26rpx;
            color: #666;
          }
          .time{
            font-size: 24rpx;
            color: #999;
          }
        }
      }
    }
    .content{
      padding:20rpx 0 20rpx 76rpx;
      font-size: 28rpx;
      border-bottom: 1px solid #dddddd;
    }
  }
}
</style>
