<template>
  <view class="index">
    <van-panel>
      <div>
        <van-field v-model="keyWord" type="seachar" placeholder="请输入关键字，拼音缩写">
          <van-button slot="button" size="small" type="primary">查询</van-button>
          <div id="panel-warp"></div>
        </van-field>

        <div class="ul-box" v-if="isShowSeach">
          <ul>
            <li>test</li>
          </ul>
        </div>
      </div>
    </van-panel>

    <div class="tag-box">
      <label>热门搜索关键字</label>
      <van-tag type="success" plain round v-for="hot in hots" :key="hot">{{hot}}</van-tag>
    </div>

    <div class="result-box" v-if="isShowSeach">
      <label class="seach-name">{{keyWord}}</label>
      <div class="img-box"></div>
      <div class="description"></div>
    </div>

    <swiper
      class="banner"
      :indicator-dots="indicatorDots"
      :autoplay="autoplay"
      :interval="interval"
      :duration="duration"
    >
      <block v-for="item in imgUrls" :key="item">
        <swiper-item>
          <image :src="item" style=" height: 500px;" class="slide-image" mode="scaleToFill"></image>
        </swiper-item>
      </block>
    </swiper>
  </view>
</template>

<script>
import card from '@/components/card'

export default {
  data () {
    return {
      keyWord: "",

      isShowSeach: false,
      hots: ["纸巾", "面膜", "鸡蛋", "剩饭", "剩菜", "所料", "小龙虾", "玻璃瓶"],

      imgUrls: [
        require('../../../static/images/可回收.png'),
        require('../../../static/images/干垃圾.png'),
        require('../../../static/images/湿垃圾.png'),
        require('../../../static/images/有害垃圾.png'),

      ],
      indicatorDots: false,
      autoplay: false,
      interval: 5000,
      duration: 1000

    }
  },

  components: {
    card
  },

  methods: {

  },
  created () {
    wx.hideTabBar();
    wx.setNavigationBarTitle({ title: '查询' });
    console.log(wx.cloud);

  },
  mounted () {



  }
}
</script>
<style lang="less" scoped>
.index {
  padding: 5px;

  #panel-warp {
    position: absolute;
  }

  .tag-box {
    margin: 20px;

    label {
      font-size: 12px;
      display: block;
      margin-bottom: 20px;
    }

    ._van-tag {
      margin: 5px;
    }
  }
  .banner {
    height: 600px;
  }
}
</style>

