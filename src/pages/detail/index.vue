<template>
  <div>
    <div class="toptitlebar">
        <!-- 背景虚化层 -->
        <div class="bg" :style="{'background-image':'url('+imgurl+')','background-size': '100% 100%', 'background-repeat': 'no-repeat'}"></div>
        <!-- 内容 -->
        <div class="baritem" v-for="(item, index) in performanceInfo" :key="index">
          <div class="baritemtop">
            <div class="themebgimg" :style="{'background-image':'url('+item.imgurl+')','background-size':'100% 100%'}"></div>
            <div class="themeinfo">
              <div class="themetitle">{{item.title}}</div>
              <div class="themeauthor">
                <!-- <image class="" src="" mode="widthFix"></image> -->
                {{item.author}} <span class="icon-right"></span>
              </div>
              <div class="viewinfo">
                <div class="viewinfoleft">{{item.num1}}人收藏</div>
                <span class="viewinfomid">|</span>
                <div class="viewinforight">已更新{{item.num2}}期</div>
              </div>
            </div>
          </div>
          <div class="baritembottom">
            <button class="sharebut"><span class="icon-share"></span> 分享</button>
            <button class="collection"><span class="icon-add"></span> 收藏</button>
          </div>
        </div>
    </div>
    <!-- 顶部选项 -->
    <div class="Performance">
      <div class="selectbar">
        <div class="detail">详情</div>
        <div class="list active">节目<span>152</span>
        </div>
      </div>
      <!-- 播放选项 -->
      <div class="play">
        <div class="playall">
          <span class="icon-video"></span> 播放全部
        </div>
        <div class="playselect">
          <div style="margin-right:20rpx"><span class="icon-order"></span> 正序</div>
          <div><span class="icon-list"></span> 选集</div>
        </div>
      </div>
      <!-- 节目列表 -->
      <div class="performanceContent" v-for="(item, index) in performance" :key="index">
        <!-- 序号 -->
        <div class="performanceIndex">{{index+1}}</div>
        <!-- 节目标题 -->
        <div class="performanceInfo">
          <div class="performanceInfoTop">
            <div style="font-size:33rpx">{{item.name}}</div>
            <div style="color:#aaaaaa">{{item.year}}</div>
          </div>
          <!-- 播放次数和时间 -->
          <div class="performanceInfoBottom">
            <div><span class="icon-video"></span>{{item.count}}</div>
            <div style="margin-left:20rpx"><span class="icon-time"></span>{{item.time}}</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      performance: [
        {
          name: '《人在江湖》郭德纲 于谦',
          year: '2年前',
          count: '5601.9万',
          time: '34:36'
        },
        {
          name: '《人在江湖》郭德纲 于谦',
          year: '2年前',
          count: '5601.9万',
          time: '34:36'
        },
        {
          name: '《人在江湖》郭德纲 于谦',
          year: '2年前',
          count: '5601.9万',
          time: '34:36'
        },
        {
          name: '《人在江湖》郭德纲 于谦',
          year: '2年前',
          count: '5601.9万',
          time: '34:36'
        },
        {
          name: '《人在江湖》郭德纲 于谦',
          year: '2年前',
          count: '5601.9万',
          time: '34:36'
        },
        {
          name: '《人在江湖》郭德纲 于谦',
          year: '2年前',
          count: '5601.9万',
          time: '34:36'
        },
        {
          name: '《人在江湖》郭德纲 于谦',
          year: '2年前',
          count: '5601.9万',
          time: '34:36'
        },
        {
          name: '《人在江湖》郭德纲 于谦',
          year: '2年前',
          count: '5601.9万',
          time: '34:36'
        },
        {
          name: '《人在江湖》郭德纲 于谦',
          year: '2年前',
          count: '5601.9万',
          time: '34:36'
        },
        {
          name: '《人在江湖》郭德纲 于谦',
          year: '2年前',
          count: '5601.9万',
          time: '34:36'
        },
        {
          name: '《人在江湖》郭德纲 于谦',
          year: '2年前',
          count: '5601.9万',
          time: '34:36'
        }
      ],
      performanceInfo: [
        {
          imgurl: 'http://imagev2.xmcdn.com/group59/M01/AC/BB/wKgLel0_rnmAmP1hAAgVnsU0jxA823.jpg',
          title: '边做游戏边学英语，好玩到停不下来',
          author: '某某某',
          num1: '767.6万',
          num2: '257'
        }
      ],
      imgurl: 'http://imagev2.xmcdn.com/group59/M01/AC/BB/wKgLel0_rnmAmP1hAAgVnsU0jxA823.jpg'
    }
  },

  components: {},

  methods: {},

  created () {
    // let app = getApp()
  }
}
</script>

<style scoped lang='scss'>
.toptitlebar {
  width: 100%;
  height: 410rpx;
  overflow: hidden;
  position: relative;
}
/* 背景虚化层 */
.bg{
  width: 100%;
  height: 410rpx;
  filter: blur(30rpx);
}
.baritem {
  width: 100%;
  height: 400rpx;
  margin-top: 50rpx;
  padding: 20rpx 0rpx;
  position: absolute;
  top: 0rpx;
}

.baritemtop {
  width: 100%;
  height: 200rpx;
  display: flex;
  justify-content: center;
  align-items: center;
}

.themebgimg {
  width: 200rpx;
  height: 200rpx;
  margin-right: 30rpx;
  background-repeat: no-repeat;
  background-size: 100% 100%;
}

.themeinfo {
  width: 60%;
  height: 200rpx;
}

.themetitle {
  color: #fff;
  font-size: 40rpx;
  display: -webkit-box;
  -webkit-line-clamp: 2;/*行数n*/
  -webkit-box-orient: vertical;
  overflow: hidden;
  text-overflow: ellipsis;
}

.themeauthor {
  font-size: 25rpx;
  color: #fff;
  margin-top: 5rpx;
}

.viewinfo {
  color: #fff;
  font-size: 30rpx;
  margin-top: 5rpx;
  display: flex;
  justify-content: flex-start;
}

.viewinfoleft {
  margin-right: 5rpx;
}

.viewinforight {
  margin-left: 5rpx;
}

.baritembottom {
  width: 70%;
  height: 100rpx;
  display: flex;
  justify-content: flex-end;
  align-items: center;
  border-radius: 20rpx;
  float: right;
  margin-top: 15rpx;
}

.baritembottom button {
  width: 210rpx;
  height: 75rpx;
  text-align: center;
  font-size: 30rpx;
  color: #fff;
  border-radius: 20rpx;
}

.sharebut {
  background: orangered;
  border: 1rpx solid #fff;
  margin-left: 70rpx;
}

.collection {
  background: orangered;
}

.Performance {
  width: 100%;
  height: 500rpx;
  border-top-left-radius: 20rpx;
  border-top-right-radius: 20rpx;
  position: relative;
  top: -10rpx;
}
.selectbar {
  width: 100%;
  height: 100rpx;
  line-height: 100rpx;
  text-align: center;
  display: flex;
  justify-content: space-between;
  background: #fff;
  box-sizing: border-box;
  color: #aaa;
  border-radius: 15rpx;
  border-bottom: 1rpx solid #f1f1f1;
}

.detail {
  width: 50%;
}

.list {
  width: 50%;
}

.play {
  width: 100%;
  height: 100rpx;
  padding: 0rpx 40rpx;
  box-sizing: border-box;
  border-bottom: 1rpx solid #f1f1f1;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.playall {
  width: auto;
  text-align: center;
  font-size: 30rpx;
}

.playselect {
  width: auto;
  display: flex;
  justify-content: space-between;
  text-align: center;
  font-size: 30rpx;
}

.performanceContent {
  width: 100%;
  height: 150rpx;
  display: flex;
  box-sizing: border-box;
  justify-content: flex-start;
  align-items: center;
  border-bottom: 1rpx solid #f1f1f1;
  padding: 20rpx 20rpx;
}

.performanceIndex {
  width: 15%;
  height: 80rpx;
  text-align: center;
  line-height: 80rpx;
  color: #aaa;
}

.performanceInfo {
  width: 85%;
  height: 100%;
}

.performanceInfoTop {
  width: 100%;
  height: 50%;
  display: flex;
  justify-content: space-between;
  font-size: 30rpx;
}

.performanceInfoBottom {
  width: 100%;
  height: auto;
  display: flex;
  justify-content: flex-start;
  color: #aaa;
  font-size: 25rpx;
  margin-top: 20rpx;
}
.active{
  position: relative;
  color: #333;
}
.active::after{
  content: '';
  width: 80rpx;
  height: 5rpx;
  position: absolute;
  bottom: 0rpx;
  left: 150rpx;
  background-color: orangered;
}
</style>
