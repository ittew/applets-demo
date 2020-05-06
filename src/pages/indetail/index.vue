<template>
  <div>
    <div class="detail-box">
      <image :src="imgurl" alt="" />
      <p class="detailtext">说到中国的红色革命根据地，我相信很多人的第一印象就是陕西的延安，因为在这里有着太多太多的故事。当然，如今的已经是一座现代与红色革命精神相拥的城市。延安不仅有闻名世界的壶口瀑布，也有宝塔山，枣园，杨家岭等革命根据地。很多人来到延安，宝塔山是必去的地方之一。它不但是延安的标志，也是革命圣地的象征......</p>
      <p class="entercon">点击更多></p>
    </div>
    <div class="detailtit">推荐主播</div>
    <div class="performanceContent" v-for="(item, index) in performance" :key="index" @tap="goPlayer(item)">
      <img class="performanceIndex" src="../../../static/images/index_icon4.png"/>
      <!-- 节目标题 -->
      <div class="performanceInfo">
        <div class="performanceInfoTop">
          <div style="font-size:33rpx">{{item.name}}</div>
          <div style="color:#aaaaaa">{{item.year}}</div>
        </div>
        <!-- 播放次数和时间 -->
        <div class="performanceInfoBottom">
          <div><img class="voiimg" src="../../../static/images/voice.png">{{item.count}}</div>
          <div style="margin-left:20rpx"><span class="icon-time"></span>{{item.time}}</div>
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
          name: '《红色延安革命根据地》王洛',
          year: '2年前',
          count: '5601.9万',
          time: '34:36'
        },
        {
          name: '《红色延安革命根据地》菲菲',
          year: '3年前',
          count: '2303万',
          time: '21:53'
        },
        {
          name: '《红色延安革命根据地》胡一天',
          year: '1个月前',
          count: '876.5万',
          time: '14:47'
        },
        {
          name: '《红色延安革命根据地》毛毛',
          year: '1年前',
          count: '601.6万',
          time: '37:38'
        },
        {
          name: '《红色延安革命根据地》碧瑶',
          year: '3年前',
          count: '456.2万',
          time: '28:51'
        },
        {
          name: '《红色延安革命根据地》沈复',
          year: '2个月前',
          count: '301.7万',
          time: '24:47'
        },
        {
          name: '《红色延安革命根据地》笑笑',
          year: '2年前',
          count: '287.6万',
          time: '64:33'
        },
        {
          name: '《红色延安革命根据地》林夕瑶',
          year: '3年前',
          count: '101.3万',
          time: '21:57'
        }
      ],
      imgurl: 'http://www.yanan.gov.cn/wcm.files/upload/CMSyanan/201710//20171024020414950.jpg'
    }
  },

  components: {},

  methods: {
    goPlayer (item) {
      console.log(item)
      wx.navigateTo({
        url: '/pages/detail/main'
      })
    }
  }
}
</script>

<style scoped lang='scss'>

.performanceContent {
  width: 100%;
  height: 150rpx;
  display: flex;
  box-sizing: border-box;
  justify-content: flex-start;
  align-items: center;
  border-bottom: 1rpx solid #f1f1f1;
  padding: 20rpx 30rpx 20rpx 20rpx;
}

.performanceIndex {
  width: 80rpx;
  height: 80rpx;
}

.performanceInfo {
  width: 88%;
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
  vertical-align: middle;
  .voiimg {
    width: 30rpx;
    height: 26rpx;
    margin-right: 10rpx;
    margin-left: 10rpx;
    margin-top: -6rpx;
    vertical-align: middle;
  }
}
.Performance .active{
  position: relative;
  color: #ff520f;
}
.Performance .active::after{
  content: '';
  width: 80rpx;
  height: 5rpx;
  position: absolute;
  bottom: 0rpx;
  left: 150rpx;
  background-color: #ff520f;
}
.detailtit{
  font-size: 35rpx;
  color: #333;
  padding: 0 0 10rpx 25rpx;
}
.detail-box{
  padding: 36rpx 36rpx 0 36rpx;
  display: flex;
  flex-direction: column;
  justify-content: center;
  .detailtext{
    text-indent: 2em;
    line-height: 45rpx;
    font-size: 30rpx;
  }
  .entercon{
    font-size: 28rpx;
    text-align: right;
    padding-right: 30rpx;
    padding-bottom: 30rpx;
    color: #333;
  }
  image{
    width: 680rpx;
    height: 480rpx;
    margin-bottom: 30rpx;
  }
}
</style>
