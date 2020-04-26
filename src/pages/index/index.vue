<template>
  <div class="index">
    <!-- 搜索框 -->
    <div class="search">
        <span class="icon-search"></span>
        <input placeholder="搜索你想听的内容">
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
      <div class="barTitle padbot20">
        <div class="Title-left">猜你喜欢</div>
        <div class="Title-right" @tap="gotoList(1)">查看全部 <span class="icon-right"></span> </div>
      </div>
      <div class="likeItemBox">
        <div class="likeItem" @tap="gotoDetails"  v-for="(v,i) in sights" :key="i">
          <div class="likeimg">
            <img class="likeItemIcon" :src="v.coverMiddle">
            <div class="likecover">
              <!-- text用来显示icon  暂无 -->
              <span class=""></span> 4.6万/人次
            </div>
          </div>
          <div class="likeText">{{v.intro}}</div>
        </div>
      </div>
    </div>
    <!-- 内容列表：旅游+教育 -->
    <div class="contentList" v-for="(v,i) in content" :key="i">
      <div class="barTitle">
        <div class="Title-left">{{v.title}}</div>
        <div class="Title-right" @tap="gotoList(i+2)">查看全部<span class="icon-right"></span></div>
      </div>
      <div v-for="(item,index) in v.list" :key="index">
        <div class="content" @tap="gotoDetails">
          <image class="contentImg" :src="item.albumCoverUrl290" mode="widthFix"></image>
          <div class="content-right">
            <div class="content-title">
              <div class="titleText">{{item.title}}</div>
              <div class="introduction">{{item.trackTitle}}</div>
            </div>
            <div class="count">
              <div class="jicount"> {{item.tracks}}万</div>
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
        '/static/images/index/ad6.jpg'
      ],
      sights: [
        {
          'intro': '西安城墙',
          'coverMiddle': 'https://pic.qyer.com/album/user/3604/0/Qk9VRhoHYkk/index/180180'
        }, {
          'intro': '陕西历史博物馆',
          'coverMiddle': 'https://pic.qyer.com/album/user/1965/51/QEBTRx8GYkA/index/180180'
        }, {
          'intro': '大唐芙蓉园',
          'coverMiddle': 'https://pic.qyer.com/album/user/3710/48/Qk5UQh4PZ0E/index/180180'
        }
      ],
      content: [
        {
          title: '红色旅游',
          list: [
            {
              'albumCoverUrl290': 'https://pic.qyer.com/album/user/3603/99/Qk9VQRMOZUk/index/180180',
              'title': '华清宫',
              'trackTitle': '高高骊山上有宫，朱楼紫殿三四重',
              'tracks': 100
            },
            {
              'albumCoverUrl290': 'https://pic.qyer.com/album/user/863/65/SU9WRB8OaA/index/180180',
              'title': '秦岭野生动物园',
              'trackTitle': '秦岭北麓。野生动物园。古城旅游的一颗璀璨明珠。',
              'tracks': 110
            },
            {
              'albumCoverUrl290': 'https://pic.qyer.com/album/user/3637/52/Qk9WRR8FYUs/index/180180',
              'title': '曲江海洋极地公园',
              'trackTitle': '欢乐的海洋之旅，将洗去你冬日的阴霾',
              'tracks': 120
            }
          ]
        },
        {
          title: '教育之声',
          list: [
            {
              'albumCoverUrl290': '/static/images/index/ed1.jpg',
              'title': '面授在线一致化',
              'trackTitle': '无论面授课还是在线课，我们都是同一套教材编写、教师培训体系，保证线上线下一致化。',
              'tracks': 100
            },
            {
              'albumCoverUrl290': '/static/images/index/ed2.jpg',
              'title': '教师教研本地化',
              'trackTitle': '依托线下教学教研体系，专注本地化的学情研究，优选本地高端师资，更适合本地孩子',
              'tracks': 110
            },
            {
              'albumCoverUrl290': '/static/images/index/ed3.jpg',
              'title': '专属班主任服务',
              'trackTitle': '授课内容针对孩子存在的障碍专项讲解，课上高频互动，关注每个孩子的学习吸收情况。',
              'tracks': 120
            }
          ]
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
    gotoList (i) {
      console.log(5555)
      // var url = e.currentTarget.dataset.coverimg
      // var title = e.currentTarget.dataset.title
      wx.switchTab({
        url: '/pages/list/main?index=' + i
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
    margin-top: 40rpx;
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
    padding-top: 20rpx;
    text-align: center;
  }
  .padbot20{
    padding-bottom: 20rpx;
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
  .icon-right {
    // background: url("") no-repeat center center;
    background-size: 64rpx 64rpx;
  }
  .like{
    width: 90%;
    margin: 0rpx auto;
    margin-top: 20rpx;
  }
  .likeItemBox{
    width: 100%;
    display: flex;
    justify-content: space-between;
    overflow: hidden;
  }
  .likeItem{
    width: 210rpx;
    height: 270rpx;
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
  /* 主要内容列表样式 */
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
    height: 210rpx;
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
    margin: 15rpx 0rpx;
    display: -webkit-box;
    -webkit-line-clamp: 1;/*行数n*/
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
  .jicount{
    font-size: 25rpx;
    color: #cdcdcd;
  }
</style>
