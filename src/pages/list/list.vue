<template>
  <div class="list">
    <div class="top-nav">
      <div class="navigate-item" v-for="(item,index) in navTitle" :key="index" @tap="handleClick(index)">
        <div class="names" :class="currentTab === index ? 'active' : ''">{{item.title}}</div>
        <div class="currtline" :class="currentTab === index ? 'active' : ''"></div>
      </div>
    </div>
    <!-- 对应的内容区 -->
    <!-- <scroll-view scroll-y> -->
      <div class="content-item"  v-for="(item,index) in currentList" :key="index">
        <div class="indexNumber">
          <div>{{index > 10 ? index : '0'+(index+1)}}</div>
        </div>
        <image :src="item.albumCoverUrl290"></image>
        <div class="content-left">
          <div class="content-title">{{item.title}}</div>
          <div class="content-text">{{item.trackTitle}}</div>
          <div class="count">
            <div style="margin-right:25rpx;">
              <!-- 本例中33.2亿的单位是写死的，此处应该是后端返回数据吧 -->
              <text class="icon-video"></text>
              <text class="">33.2亿</text>
            </div>
            <div>
              <text class="icon"></text>
              <text class="">44集</text>
            </div>
          </div>
        </div>
      </div>
    <!-- </scroll-view> -->
  </div>
</template>

<script>

export default {
  data () {
    return {
      currentTab: 0,
      navTitle: [
        {title: '儿童教育'},
        {title: '人文历史'},
        {title: '最潮外语'}
      ],
      currentList: [],
      listData: [
        {
          'hotRecommends': {
            'list': [
              {
                'albumCoverUrl290': 'http://imagev2.xmcdn.com/group66/M02/5F/87/wKgMdV1k-SryG2bxAANsUR5aOuY490.jpg!op_type=5&upload_type=album&device_type=ios&name=medium&magick=png',
                'title': '《长宁帝军》| 江湖范儿热血爽文',
                'trackTitle': '今日，谁与我共同浴血，谁就是我的兄弟'
              },
              {
                'albumCoverUrl290': 'http://imagev2.xmcdn.com/group59/M0A/AE/A4/wKgLel0_6jSB96guAAQiVnZ8T6o580.jpg!op_type=5&upload_type=album&device_type=ios&name=medium&magick=png',
                'title': '绝世高手【头陀渊】免费有声小说',
                'trackTitle': '男女双播，都市玄幻，修真神作'
              },
              {
                'albumCoverUrl290': 'http://imagev2.xmcdn.com/group59/M0A/AE/A4/wKgLel0_6jSB96guAAQiVnZ8T6o580.jpg!op_type=5&upload_type=album&device_type=ios&name=medium&magick=png',
                'title': '绝世高手【头陀渊】免费有声小说',
                'trackTitle': '男女双播，都市玄幻，修真神作'
              },
              {
                'albumCoverUrl290': 'http://imagev2.xmcdn.com/group59/M0A/AE/A4/wKgLel0_6jSB96guAAQiVnZ8T6o580.jpg!op_type=5&upload_type=album&device_type=ios&name=medium&magick=png',
                'title': '绝世高手【头陀渊】免费有声小说',
                'trackTitle': '男女双播，都市玄幻，修真神作'
              },
              {
                'albumCoverUrl290': 'http://imagev2.xmcdn.com/group59/M0A/AE/A4/wKgLel0_6jSB96guAAQiVnZ8T6o580.jpg!op_type=5&upload_type=album&device_type=ios&name=medium&magick=png',
                'title': '绝世高手【头陀渊】免费有声小说',
                'trackTitle': '男女双播，都市玄幻，修真神作'
              },
              {
                'albumCoverUrl290': 'http://imagev2.xmcdn.com/group59/M0A/AE/A4/wKgLel0_6jSB96guAAQiVnZ8T6o580.jpg!op_type=5&upload_type=album&device_type=ios&name=medium&magick=png',
                'title': '绝世高手【头陀渊】免费有声小说',
                'trackTitle': '男女双播，都市玄幻，修真神作'
              },
              {
                'albumCoverUrl290': 'http://imagev2.xmcdn.com/group59/M0A/AE/A4/wKgLel0_6jSB96guAAQiVnZ8T6o580.jpg!op_type=5&upload_type=album&device_type=ios&name=medium&magick=png',
                'title': '绝世高手【头陀渊】免费有声小说',
                'trackTitle': '男女双播，都市玄幻，修真神作'
              },
              {
                'albumCoverUrl290': 'http://imagev2.xmcdn.com/group59/M0A/AE/A4/wKgLel0_6jSB96guAAQiVnZ8T6o580.jpg!op_type=5&upload_type=album&device_type=ios&name=medium&magick=png',
                'title': '绝世高手【头陀渊】免费有声小说',
                'trackTitle': '男女双播，都市玄幻，修真神作'
              },
              {
                'albumCoverUrl290': 'http://imagev2.xmcdn.com/group59/M0A/AE/A4/wKgLel0_6jSB96guAAQiVnZ8T6o580.jpg!op_type=5&upload_type=album&device_type=ios&name=medium&magick=png',
                'title': '绝世高手【头陀渊】免费有声小说',
                'trackTitle': '男女双播，都市玄幻，修真神作'
              }
            ]
          }
        },
        {
          'hotRecommends': {
            'list': [
              {
                'albumCoverUrl290': 'http://imagev2.xmcdn.com/group66/M02/5F/87/wKgMdV1k-SryG2bxAANsUR5aOuY490.jpg!op_type=5&upload_type=album&device_type=ios&name=medium&magick=png',
                'title': '《长宁帝军》| 江湖范儿热血爽文',
                'trackTitle': '今日，谁与我共同浴血，谁就是我的兄弟'
              },
              {
                'albumCoverUrl290': 'http://imagev2.xmcdn.com/group59/M0A/AE/A4/wKgLel0_6jSB96guAAQiVnZ8T6o580.jpg!op_type=5&upload_type=album&device_type=ios&name=medium&magick=png',
                'title': '22222222222222222222',
                'trackTitle': '男女双播，都市玄幻，修真神作'
              },
              {
                'albumCoverUrl290': 'http://imagev2.xmcdn.com/group59/M0A/AE/A4/wKgLel0_6jSB96guAAQiVnZ8T6o580.jpg!op_type=5&upload_type=album&device_type=ios&name=medium&magick=png',
                'title': '22222222222222222222',
                'trackTitle': '男女双播，都市玄幻，修真神作'
              },
              {
                'albumCoverUrl290': 'http://imagev2.xmcdn.com/group59/M0A/AE/A4/wKgLel0_6jSB96guAAQiVnZ8T6o580.jpg!op_type=5&upload_type=album&device_type=ios&name=medium&magick=png',
                'title': '22222222222222222222',
                'trackTitle': '男女双播，都市玄幻，修真神作'
              },
              {
                'albumCoverUrl290': 'http://imagev2.xmcdn.com/group59/M0A/AE/A4/wKgLel0_6jSB96guAAQiVnZ8T6o580.jpg!op_type=5&upload_type=album&device_type=ios&name=medium&magick=png',
                'title': '2222222222222222',
                'trackTitle': '男女双播，都市玄幻，修真神作'
              },
              {
                'albumCoverUrl290': 'http://imagev2.xmcdn.com/group59/M0A/AE/A4/wKgLel0_6jSB96guAAQiVnZ8T6o580.jpg!op_type=5&upload_type=album&device_type=ios&name=medium&magick=png',
                'title': '2222222222222222',
                'trackTitle': '男女双播，都市玄幻，修真神作'
              },
              {
                'albumCoverUrl290': 'http://imagev2.xmcdn.com/group59/M0A/AE/A4/wKgLel0_6jSB96guAAQiVnZ8T6o580.jpg!op_type=5&upload_type=album&device_type=ios&name=medium&magick=png',
                'title': '22222222222222222222222222222222',
                'trackTitle': '男女双播，都市玄幻，修真神作'
              },
              {
                'albumCoverUrl290': 'http://imagev2.xmcdn.com/group59/M0A/AE/A4/wKgLel0_6jSB96guAAQiVnZ8T6o580.jpg!op_type=5&upload_type=album&device_type=ios&name=medium&magick=png',
                'title': '22222222222222222222222222222222',
                'trackTitle': '男女双播，都市玄幻，修真神作'
              },
              {
                'albumCoverUrl290': 'http://imagev2.xmcdn.com/group59/M0A/AE/A4/wKgLel0_6jSB96guAAQiVnZ8T6o580.jpg!op_type=5&upload_type=album&device_type=ios&name=medium&magick=png',
                'title': '222222222222',
                'trackTitle': '男女双播，都市玄幻，修真神作'
              }
            ]
          }
        },
        {
          'hotRecommends': {
            'list': [
              {
                'albumCoverUrl290': 'http://imagev2.xmcdn.com/group66/M02/5F/87/wKgMdV1k-SryG2bxAANsUR5aOuY490.jpg!op_type=5&upload_type=album&device_type=ios&name=medium&magick=png',
                'title': '《长宁帝军》| 江湖范儿热血爽文',
                'trackTitle': '今日，谁与我共同浴血，谁就是我的兄弟'
              },
              {
                'albumCoverUrl290': 'http://imagev2.xmcdn.com/group59/M0A/AE/A4/wKgLel0_6jSB96guAAQiVnZ8T6o580.jpg!op_type=5&upload_type=album&device_type=ios&name=medium&magick=png',
                'title': '33333333333333333',
                'trackTitle': '男女双播，都市玄幻，修真神作'
              },
              {
                'albumCoverUrl290': 'http://imagev2.xmcdn.com/group59/M0A/AE/A4/wKgLel0_6jSB96guAAQiVnZ8T6o580.jpg!op_type=5&upload_type=album&device_type=ios&name=medium&magick=png',
                'title': '333333333333333333333333',
                'trackTitle': '男女双播，都市玄幻，修真神作'
              },
              {
                'albumCoverUrl290': 'http://imagev2.xmcdn.com/group59/M0A/AE/A4/wKgLel0_6jSB96guAAQiVnZ8T6o580.jpg!op_type=5&upload_type=album&device_type=ios&name=medium&magick=png',
                'title': '333333333333333333333333',
                'trackTitle': '男女双播，都市玄幻，修真神作'
              },
              {
                'albumCoverUrl290': 'http://imagev2.xmcdn.com/group59/M0A/AE/A4/wKgLel0_6jSB96guAAQiVnZ8T6o580.jpg!op_type=5&upload_type=album&device_type=ios&name=medium&magick=png',
                'title': '333333333333333333333333',
                'trackTitle': '男女双播，都市玄幻，修真神作'
              },
              {
                'albumCoverUrl290': 'http://imagev2.xmcdn.com/group59/M0A/AE/A4/wKgLel0_6jSB96guAAQiVnZ8T6o580.jpg!op_type=5&upload_type=album&device_type=ios&name=medium&magick=png',
                'title': '333333333333333333333333',
                'trackTitle': '男女双播，都市玄幻，修真神作'
              },
              {
                'albumCoverUrl290': 'http://imagev2.xmcdn.com/group59/M0A/AE/A4/wKgLel0_6jSB96guAAQiVnZ8T6o580.jpg!op_type=5&upload_type=album&device_type=ios&name=medium&magick=png',
                'title': '333333333333333333333333',
                'trackTitle': '男女双播，都市玄幻，修真神作'
              },
              {
                'albumCoverUrl290': 'http://imagev2.xmcdn.com/group59/M0A/AE/A4/wKgLel0_6jSB96guAAQiVnZ8T6o580.jpg!op_type=5&upload_type=album&device_type=ios&name=medium&magick=png',
                'title': '333333333333333333333333',
                'trackTitle': '男女双播，都市玄幻，修真神作'
              },
              {
                'albumCoverUrl290': 'http://imagev2.xmcdn.com/group59/M0A/AE/A4/wKgLel0_6jSB96guAAQiVnZ8T6o580.jpg!op_type=5&upload_type=album&device_type=ios&name=medium&magick=png',
                'title': '333333333333333333333333',
                'trackTitle': '男女双播，都市玄幻，修真神作'
              }
            ]
          }
        }
      ]
    }
  },
  beforeMount () {
    this.currentList = this.listData[0].hotRecommends.list
  },
  methods: {
    // 跳转商品详情页面
    handleClick (i) {
      this.currentTab = i
      this.currentList = this.listData[i].hotRecommends.list
      console.log(this.currentList)
    }
  }
}
</script>
<style lang="scss">
  page {
    // background-color: #0f0;
    height: 100%;
  }
  .top-nav{
    width: 100%;
    height: 80rpx;
    display: flex;
  }
  .navigate-item {
    flex:1;
    text-align: center;
    height: 90rpx;
    line-height: 90rpx;
  }

  .names {
    font-size: 28rpx;
    color: #3c3c3c;
  }

  .names.active {
    color: #ff520f;
    font-weight: bold;
    font-size: 34rpx;
  }

  .currtline {
    margin: -8rpx auto 0 auto;
    width: 100rpx;
    height: 1rpx;
    border-radius: 4rpx;
  }

  .currtline.active {
    background: #ff520f;
    transition: all .3s;
  }
  .content-item{
    width: 100%;
    display: flex;
    justify-content: space-around;
    align-items: center;
    padding: 20rpx 0rpx;
  }

  .indexNumber {
    width: 15%;
    height: auto;
    padding: 20rpx 0rpx;
    text-align: center;
    font-size: 50rpx;
    color: #ff520f;
  }

  .content-item image {
    width: 140rpx;
    height: 140rpx;
    margin-top: 10rpx;
    border-radius: 15rpx;
  }

  .content-left {
    padding: 10rpx 0rpx;
    margin-left: 30rpx;
    width: 60%;
    height: auto;
    border-bottom: 1rpx solid #f1f1f1;
  }

  .content-title{
    font-size: 35rpx;
    height: 40rpx;
    color: #000;
    display: -webkit-box;
    -webkit-line-clamp: 2;/*行数n*/
    -webkit-box-orient: vertical;
    overflow: hidden;
    text-overflow: ellipsis;
  }
  .content-text{
    height: 40rpx;
    display: -webkit-box;
    -webkit-line-clamp: 1;/*行数n*/
    -webkit-box-orient: vertical;
    overflow: hidden;
    text-overflow: ellipsis;
    font-size: 27rpx;
    text-align: left;
    color: #ccc;
    margin-top: 15rpx;
  }
  .count{
    font-size: 27rpx;
    color: #ccc;
    display: flex;
    justify-content: start;
    margin-top: 15rpx;
  }
</style>
