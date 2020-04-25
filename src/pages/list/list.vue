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
      <div class="content-item" @tap="gotoDetails"  v-for="(item,index) in currentList" :key="index">
        <!-- <div class="indexNumber">
          <div>{{index > 10 ? index : '0'+(index+1)}}</div>
        </div> -->
        <image :src="item.albumCoverUrl290" />
        <div class="content-left">
          <div class="content-title">{{item.title}}</div>
          <div class="content-text">{{item.trackTitle}}</div>
          <div class="count">
            <div style="margin-right:25rpx;">
              <!-- 本例中33.2亿的单位是写死的，此处应该是后端返回数据吧 -->
              <text class="icon-video"></text>
              <text class="">33.2万</text>
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
        {title: '猜你喜欢'},
        {title: '陕西旅游'},
        {title: '陕西教育'}
      ],
      currentList: [],
      listData: [
        {
          'hotRecommends': {
            'list': [
              {
                'albumCoverUrl290': '/static/images/list/list1.jpg',
                'title': '西安钟楼',
                'trackTitle': '中国古代遗留的形制最大、保存最完整的一座钟楼，每天都有6场编钟表演。'
              },
              {
                'albumCoverUrl290': '/static/images/list/list2.jpeg',
                'title': '西安小雁塔',
                'trackTitle': '环境清幽，经受了1200多年风雨的侵袭和70余次地震的考验，历史上曾经历过三次离合。'
              },
              {
                'albumCoverUrl290': '/static/images/list/list3.jpg',
                'title': '西安城墙',
                'trackTitle': '古城墙历史悠久，登上城墙，感受到了历史的魅力，城墙很宽阔，俯瞰西安城很不错！'
              },
              {
                'albumCoverUrl290': '/static/images/list/list1.jpg',
                'title': '西安钟楼',
                'trackTitle': '中国古代遗留的形制最大、保存最完整的一座钟楼，每天都有6场编钟表演。'
              },
              {
                'albumCoverUrl290': '/static/images/list/list2.jpeg',
                'title': '西安小雁塔',
                'trackTitle': '环境清幽，经受了1200多年风雨的侵袭和70余次地震的考验，历史上曾经历过三次离合。'
              },
              {
                'albumCoverUrl290': '/static/images/list/list3.jpg',
                'title': '西安城墙',
                'trackTitle': '古城墙历史悠久，登上城墙，感受到了历史的魅力，城墙很宽阔，俯瞰西安城很不错！'
              },
              {
                'albumCoverUrl290': '/static/images/list/list2.jpeg',
                'title': '西安小雁塔',
                'trackTitle': '环境清幽，经受了1200多年风雨的侵袭和70余次地震的考验，历史上曾经历过三次离合。'
              },
              {
                'albumCoverUrl290': '/static/images/list/list3.jpg',
                'title': '西安城墙',
                'trackTitle': '古城墙历史悠久，登上城墙，感受到了历史的魅力，城墙很宽阔，俯瞰西安城很不错！'
              },
              {
                'albumCoverUrl290': '/static/images/list/list1.jpg',
                'title': '西安钟楼',
                'trackTitle': '中国古代遗留的形制最大、保存最完整的一座钟楼，每天都有6场编钟表演。'
              }
            ]
          }
        },
        {
          'hotRecommends': {
            'list': [
              {
                'albumCoverUrl290': 'https://pic.qyer.com/album/user/3603/99/Qk9VQRMOZUk/index/180180',
                'title': '华清宫',
                'trackTitle': '高高骊山上有宫，朱楼紫殿三四重'
              },
              {
                'albumCoverUrl290': 'https://pic.qyer.com/album/user/863/65/SU9WRB8OaA/index/180180',
                'title': '秦岭野生动物园',
                'trackTitle': '秦岭北麓。野生动物园。古城旅游的一颗璀璨明珠。'
              },
              {
                'albumCoverUrl290': 'https://pic.qyer.com/album/user/3637/52/Qk9WRR8FYUs/index/180180',
                'title': '曲江海洋极地公园',
                'trackTitle': '欢乐的海洋之旅，将洗去你冬日的阴霾'
              },
              {
                'albumCoverUrl290': 'https://pic.qyer.com/album/user/3603/99/Qk9VQRMOZUk/index/180180',
                'title': '华清宫',
                'trackTitle': '高高骊山上有宫，朱楼紫殿三四重'
              },
              {
                'albumCoverUrl290': 'https://pic.qyer.com/album/user/863/65/SU9WRB8OaA/index/180180',
                'title': '秦岭野生动物园',
                'trackTitle': '秦岭北麓。野生动物园。古城旅游的一颗璀璨明珠。'
              },
              {
                'albumCoverUrl290': 'https://pic.qyer.com/album/user/3637/52/Qk9WRR8FYUs/index/180180',
                'title': '曲江海洋极地公园',
                'trackTitle': '欢乐的海洋之旅，将洗去你冬日的阴霾'
              },
              {
                'albumCoverUrl290': 'https://pic.qyer.com/album/user/3603/99/Qk9VQRMOZUk/index/180180',
                'title': '华清宫',
                'trackTitle': '高高骊山上有宫，朱楼紫殿三四重'
              },
              {
                'albumCoverUrl290': 'https://pic.qyer.com/album/user/863/65/SU9WRB8OaA/index/180180',
                'title': '秦岭野生动物园',
                'trackTitle': '秦岭北麓。野生动物园。古城旅游的一颗璀璨明珠。'
              },
              {
                'albumCoverUrl290': 'https://pic.qyer.com/album/user/3637/52/Qk9WRR8FYUs/index/180180',
                'title': '曲江海洋极地公园',
                'trackTitle': '欢乐的海洋之旅，将洗去你冬日的阴霾'
              }
            ]
          }
        },
        {
          'hotRecommends': {
            'list': [
              {
                'albumCoverUrl290': '/static/images/index/ed1.png',
                'title': '面授在线一致化',
                'trackTitle': '无论面授课还是在线课，我们都是同一套教材编写、教师培训体系，保证线上线下一致化。'
              },
              {
                'albumCoverUrl290': '/static/images/index/ed2.png',
                'title': '教师教研本地化',
                'trackTitle': '依托线下教学教研体系，专注本地化的学情研究，优选本地高端师资，更适合本地孩子'
              },
              {
                'albumCoverUrl290': '/static/images/index/ed3.png',
                'title': '专属班主任服务',
                'trackTitle': '授课内容针对孩子存在的障碍专项讲解，课上高频互动，关注每个孩子的学习吸收情况。'
              },
              {
                'albumCoverUrl290': '/static/images/index/ed1.png',
                'title': '面授在线一致化',
                'trackTitle': '无论面授课还是在线课，我们都是同一套教材编写、教师培训体系，保证线上线下一致化。'
              },
              {
                'albumCoverUrl290': '/static/images/index/ed2.png',
                'title': '教师教研本地化',
                'trackTitle': '依托线下教学教研体系，专注本地化的学情研究，优选本地高端师资，更适合本地孩子'
              },
              {
                'albumCoverUrl290': '/static/images/index/ed3.png',
                'title': '专属班主任服务',
                'trackTitle': '授课内容针对孩子存在的障碍专项讲解，课上高频互动，关注每个孩子的学习吸收情况。'
              },
              {
                'albumCoverUrl290': '/static/images/index/ed1.png',
                'title': '面授在线一致化',
                'trackTitle': '无论面授课还是在线课，我们都是同一套教材编写、教师培训体系，保证线上线下一致化。'
              },
              {
                'albumCoverUrl290': '/static/images/index/ed2.png',
                'title': '教师教研本地化',
                'trackTitle': '依托线下教学教研体系，专注本地化的学情研究，优选本地高端师资，更适合本地孩子'
              },
              {
                'albumCoverUrl290': '/static/images/index/ed3.png',
                'title': '专属班主任服务',
                'trackTitle': '授课内容针对孩子存在的障碍专项讲解，课上高频互动，关注每个孩子的学习吸收情况。'
              }
            ]
          }
        }
      ]
    }
  },
  beforeMount () {
    // this.currentTab = this.$router.query.index
    this.currentList = this.listData[0].hotRecommends.list
  },
  methods: {
    // 跳转商品详情页面
    gotoDetails () {
      wx.navigateTo({
        url: '/pages/detail/main'
      })
    },
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
    width: 150rpx;
    height: 150rpx;
    margin-top: 10rpx;
    border-radius: 15rpx;
  }

  .content-left {
    padding: 10rpx 0rpx;
    width: 70%;
    height: auto;
    border-bottom: 1rpx solid #f1f1f1;
  }

  .content-title{
    font-size: 35rpx;
    // height: 40rpx;
    color: #000;
    display: -webkit-box;
    -webkit-line-clamp: 2;/*行数n*/
    -webkit-box-orient: vertical;
    overflow: hidden;
    text-overflow: ellipsis;
  }
  .content-text{
    // height: 40rpx;
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
