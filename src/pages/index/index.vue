<template>
  <div class="index">
    <!-- 搜索框 -->
    <div class="search">
        <span class="icon-search"></span>
        <input placeholder="搜索你想听的节目">
    </div>
    <!-- 轮播图 -->
    <div class="swiper-container">
      <swiper class="swiper" autoplay="true" circular="true"
        interval="3000" easing-function="easeOutCubic"
        @change="swiperChange">
        <!-- 轮播图图片 -->
        <swiper-item class="swiperItem" v-for="(v,i) in imgList" :key="i">
          <!-- 加上widthFix可以使图片自适应 -->
          <img :src="v" alt="">
        </swiper-item>
      </swiper>
      <!-- 为了和喜马拉雅一致，自己需定制轮播图dots -->
      <div class="dots">
        <div v-for="(v,i) in imgList" :key="i">
          <div class="dotsItem" :class="i == swiperCurrent ? ' dotActive' : ''"></div>
        </div>
      </div>
    </div>
    <!-- 猜你喜欢 -->
    <div class="like">
      <div class="barTitle">
        <div class="Title-left">猜你喜欢</div>
        <div class="Title-right" @tap="gotoList">查看全部 <text class="icon-right"></text> </div>
      </div>
      <div class="likeItemBox">
        <div class="likeItem" @tap="gotoDetails"  v-for="(v,i) in guess" :key="i">
          <div class="likeimg">
            <img class="likeItemIcon" :src="v.coverMiddle">
            <div class="likecover">
              <!-- text用来显示icon  暂无 -->
              <text class=""></text> 4.6亿
            </div>
          </div>
          <div class="likeText">{{v.intro}}</div>
        </div>
      </div>
    </div>
    <!-- 有声小说 -->
    <div class="contentList">
      <div class="barTitle">
        <div class="Title-left">有声小说</div>
        <div class="Title-right" @tap="gotoList">查看全部<text class="icon-right"></text></div>
      </div>
      <div v-for="(item,index) in novel" :key="index">
        <div class="content" @tap="gotoDetails">
          <div class="contentImg">
            <image :src="item.albumCoverUrl290" mode="widthFix"></image>
          </div>
          <div class="content-right">
            <div class="content-title">
              <div class="titleText">{{item.title}}</div>
              <div class="introduction">{{item.trackTitle}}</div>
            </div>
            <div class="count">
              <div class="playcount">
                <!-- <text class="icon-"></text> -->
                126亿
              </div>
              <div class="jicount">{{item.tracks}}集</div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- 旅游 -->
    <div class="contentList">
      <div class="barTitle">
        <div class="Title-left">旅游</div>
        <div class="Title-right" @tap="gotoList">查看全部<text class="icon-right"></text></div>
      </div>
      <div v-for="(item,index) in novel" :key="index">
        <div class="content" @tap="gotoDetails">
          <div class="contentImg">
            <image :src="item.albumCoverUrl290" mode="widthFix"></image>
          </div>
          <div class="content-right">
            <div class="content-title">
              <div class="titleText">{{item.title}}</div>
              <div class="introduction">{{item.trackTitle}}</div>
            </div>
            <div class="count">
              <div class="playcount">
                <!-- <text class="icon-"></text> -->
                126亿
              </div>
              <div class="jicount">{{item.tracks}}集</div>
            </div>
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
      imgList: [
        '/static/images/index/ad1.jpg',
        '/static/images/index/ad2.jpg',
        '/static/images/index/ad3.jpg',
        '/static/images/index/ad4.jpg',
        '/static/images/index/ad5.jpg',
        '/static/images/index/ad6.jpg',
        '/static/images/index/ad7.jpg'
      ],
      guess: [
        {
          'intro': '聪明宝宝从胎教音乐开始',
          'coverMiddle': 'http://imagev2.xmcdn.com/group32/M08/28/BB/wKgJS1muRorAI1jPAAKG8d9Exac241.png!op_type=5&upload_type=album&device_type=ios&name=medium&magick=png'
        }, {
          'intro': '聪明宝宝从胎教音乐开始',
          'coverMiddle': 'http://imagev2.xmcdn.com/group32/M08/28/BB/wKgJS1muRorAI1jPAAKG8d9Exac241.png!op_type=5&upload_type=album&device_type=ios&name=medium&magick=png'
        }, {
          'intro': '聪明宝宝从胎教音乐开始',
          'coverMiddle': 'http://imagev2.xmcdn.com/group32/M08/28/BB/wKgJS1muRorAI1jPAAKG8d9Exac241.png!op_type=5&upload_type=album&device_type=ios&name=medium&magick=png'
        }
      ],
      novel: [
        {
          'albumCoverUrl290': 'http://imagev2.xmcdn.com/group66/M02/5F/87/wKgMdV1k-SryG2bxAANsUR5aOuY490.jpg!op_type=5&upload_type=album&device_type=ios&name=medium&magick=png',
          'title': '《长宁帝军》| 江湖范儿热血爽文',
          'trackTitle': '今日，谁与我共同浴血，谁就是我的兄弟',
          'tracks': 100
        },
        {
          'albumCoverUrl290': 'http://imagev2.xmcdn.com/group66/M02/5F/87/wKgMdV1k-SryG2bxAANsUR5aOuY490.jpg!op_type=5&upload_type=album&device_type=ios&name=medium&magick=png',
          'title': '《长宁帝军》| 江湖范儿热血爽文',
          'trackTitle': '今日，谁与我共同浴血，谁就是我的兄弟',
          'tracks': 100
        },
        {
          'albumCoverUrl290': 'http://imagev2.xmcdn.com/group66/M02/5F/87/wKgMdV1k-SryG2bxAANsUR5aOuY490.jpg!op_type=5&upload_type=album&device_type=ios&name=medium&magick=png',
          'title': '《长宁帝军》| 江湖范儿热血爽文',
          'trackTitle': '今日，谁与我共同浴血，谁就是我的兄弟',
          'tracks': 100
        }
      ],
      swiperCurrent: 0
    }
  },
  methods: {
    // 轮播图改变事件
    swiperChange (e) {
      this.swiperCurrent = e.mp.detail.current
    },
    // 跳转商品详情页面
    gotoDetails () {
      // var url = e.currentTarget.dataset.coverimg
      // var title = e.currentTarget.dataset.title
      wx.navigateTo({
        url: '/pages/detail/main'
      })
    },
    // 跳转商品详情页面
    gotoList () {
      console.log(5555)
      // var url = e.currentTarget.dataset.coverimg
      // var title = e.currentTarget.dataset.title
      wx.switchTab({
        url: '/pages/list/main'
      })
    }
  }
}
</script>
<style lang="scss">
  page {
    // background-color: #0f0;
    height: 100%;
  }
  /* 搜索框 */
  .search{
    width: 90%;
    display: flex;
    align-items: center;
    margin: 0 auto;
    // margin-left: 5%;
    // margin-top: 20px;
    background-color: rgb(240, 240, 240);
    padding: 10rpx 20rpx;
    border-radius: 15rpx;
  }

  .search input{
    width: 90%;
    height: 100%;
    font-size: 29rpx;
    margin-left: 20rpx;
  }
  // 轮播图
  .swiper-container{
    width: 90%;
    height: 280rpx;
    margin: 0rpx auto;
    margin-top: 30px;
    position: relative;
    border-radius: 15rpx;
    overflow: hidden;
  }
  .swiper{
    width: 100%;
    height: 100%;
    border-radius: 15rpx;
  }
  .swiperItem{
    width: 100%;
    height: 100%;
    border-radius: 15rpx;
  }
  .swiperItem>img{
    width: 100%;
    height: 100%;
    border-radius: 15rpx;
  }
  .dots{
    width: auto;
    height: 10rpx;
    position: absolute;
    bottom: 20rpx;
    border-radius: 50rpx;
    left: 240rpx;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 3rpx 10rpx;
  }
  .dotsItem{
    width: 8rpx;
    height: 8rpx;
    margin: 0rpx 8rpx;
    border-radius: 50%;
    background-color: #cdcdcd;
    transition: all .3s;
  }
  .dotActive{
    width: 10rpx;
    height: 10rpx;
    background-color: #fff;
  }
  // 猜你喜欢
  .barTitle {
    width: 100%;
    height: 56rpx;
    padding: 20rpx 0rpx;
    text-align: center;
  }
  .Title-left {
    float: left;
    font-size: 37rpx;
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    font-weight: 800;
    color: #333;
  }

  .Title-right {
    float: right;
    font-size: 26rpx;
    color: #aaa;
  }
  .like{
    width: 90%;
    margin: 0rpx auto;
    margin-top: 40rpx;
  }
  .likeItemBox{
    width: 100%;
    display: flex;
    justify-content: space-between;
    overflow: hidden;
  }
  .likeItem{
    width: 210rpx;
    height: 310rpx;
    border-radius: 15rpx;
  }
  .likeimg{
    width: 210rpx;
    height: 210rpx;
    border-radius: 15rpx;
    position: relative;
  }
  .likeItemIcon{
    width: 100%;
    height: 100%;
    border-radius: 15rpx;
  }
  .likeText{
    font-size: 28rpx;
    color: #333;
    margin-top: 10rpx;
    display: -webkit-box;
    -webkit-line-clamp: 2;/*行数n*/
    -webkit-box-orient: vertical;
    overflow: hidden;
    text-overflow: ellipsis;
  }
  .likecover{
    width: 190rpx;
    height: 40rpx;
    /* 透明背景层 */
    background-image: linear-gradient(rgba(0, 0, 0, 0.01), rgba(0, 0, 0, 1));
    /* opacity: 0.3; */
    position: absolute;
    bottom: 0rpx;
    color: #fff;
    font-size: 25rpx;
    padding: 5rpx 10rpx;
    border-bottom-left-radius: 15rpx;
    border-bottom-right-radius: 15rpx;
  }
  .dataNotip{
    width: 100%;
    height: 300rpx;
    padding-top: 150rpx;
  }
  .tip{
    width: auto;
    height: 100rpx;
    text-align: center;
    margin: 0rpx auto;
    color: red;
    font-weight: 800;
  }
  /* 有声小说-主要内容列表样式 */
  .contentList{
    width: 90%;
    height: auto;
    margin: 0rpx auto;
  }
  .content{
    width: 100%;
    height: auto;
    padding: 20rpx 0rpx;
    display: flex;
    justify-content: space-between;
    border-bottom: 1rpx solid #f1f1f1;
  }
  .contentImg{
    width: 232rpx;
    height: 232rpx;
    border-radius: 15rpx;
  }
  .contentImg>image{
    width: 100%;
    height: 100%;
    border-radius: 15rpx;
  }
  .content-right{
    width: 530rpx;
    height: 100%;
    margin-left: 20rpx;
    display: flex;
    flex-direction: column;
  }
  .content-title{
    width: 100%;
    height: 138rpx;
    overflow: hidden;
    display: flex;
    flex-direction: column;
  }
  .titleText{
    width: 100%;
    font-size: 35rpx;
    color: #333;
    text-align: left;
    display: -webkit-box;
    -webkit-line-clamp: 1;/*行数n*/
    -webkit-box-orient: vertical;
    overflow: hidden;
    text-overflow: ellipsis;
  }
  .introduction{
    width: 100%;
    font-size: 28rpx;
    color: #cdcdcd;
    text-align: left;
    padding: 15rpx 0rpx;
    display: -webkit-box;
    -webkit-line-clamp: 2;/*行数n*/
    -webkit-box-orient: vertical;
    overflow: hidden;
    text-overflow: ellipsis;
  }
  .count{
    width: 100%;
    height: 50rpx;
    display: flex;
    justify-content: start;
    align-items: center;
  }
  .playcount{
  font-size: 25rpx;
  color: #cdcdcd;
  margin-right: 30rpx;
  }
  .jicount{
    font-size: 25rpx;
    color: #cdcdcd;
  }
</style>
