<template>
  <div class="contentList">
    <van-nav-bar title="考核评估">
      <span slot="right" class="iconfont iconduansousuo"></span>
    </van-nav-bar>
    <van-tabs v-model="active" title-active-color="#377fed" color="#377fed" line-height="2">
      <van-tab title="全部">
        <div class="xiangmu">
          <div class="item-box" v-for="(item,index) in items" :key="index">
            <div :class="item.style" class="img"></div>
            <h2>{{item.name}}</h2>
            <p>
              共<span>{{item.gong}}</span>家(
              <span>{{item.gong}}</span>/
              <span>{{item.er}}</span>/
              <span>{{item.san}}</span>，未开始/进行中/已完成)
            </p>
            <div class="jindu">
              <van-progress :percentage="50" stroke-width="5" :show-pivot="false" />
              <span class="red">10%</span>
            </div>
            <div class="buttons">
              <div class="button-box">
                <span class="iconfont iconjibenxinxi"></span>
                <span class="text">考核进度</span>
              </div>
                 <div class="button-box">
                <span class="iconfont iconfenjie"></span>
                <span class="text">考核结果</span>
              </div>
            </div>
          </div>
        </div>
      </van-tab>
      <van-tab title="未开始"></van-tab>
      <van-tab title="进行中"></van-tab>
      <van-tab title="已完成"></van-tab>
    </van-tabs>
  </div>
</template>
<script>
import Vue from "vue";
import Vant from "vant";
import "vant/lib/index.css";

Vue.use(Vant);
export default {
  name: "contentList",
  list: [{ title: "11223" }],
  loading: false,
  finished: false,
  name: "login",
  data() {
    return {
      items: [
        {
          name: "杭州市政府数字化转型工作评价考核指标-区县(市)",
          gong: "52",
          er: "0",
          san: "0",
          style:'ready'
        },
           {
          name: "杭州市政府数字化转型工作评价考核指标-区县(市)",
          gong: "52",
          er: "0",
          san: "0",
          style:'doing'
        },
           {
          name: "杭州市政府数字化转型工作评价考核指标-区县(市)",
          gong: "52",
          er: "0",
          san: "0",
          style:'end'
        },
              {
          name: "杭州市政府数字化转型工作评价考核指标-区县(市)",
          gong: "52",
          er: "0",
          san: "0",
          style:'doing'
        },
      ],
      active: 0
    };
  },
  methods: {
    changeTag(index) {
      let that = this;
      that.tagIndex = index;
      // 请求接口，获得contentList数据
      that.getData();
    },
    getData() {
      let that = this;
      // 搜索的方法获得数据
      // getEvals(that.$refs.mainTemp.searchValue, that.tagList[that.active].id ==0 ? '': that.tagList[that.active].id ).then((res) => {
      //   that.allList =res.data.records
      // })
      that.isLoading = false;
    },
    onClickLeft() {
      Toast("返回");
    },
    onClickRight() {
      Toast("更多");
    }
  },
  onLoad() {
    // 异步更新数据
    // setTimeout 仅做示例，真实场景中一般为 ajax 请求
    setTimeout(() => {
      for (let i = 0; i < 10; i++) {
        this.list.push(this.list.length + 1);
      }

      // 加载状态结束
      this.loading = false;

      // 数据全部加载完成
      if (this.list.length >= 40) {
        this.finished = true;
      }
    }, 1000);
  }
};
</script>
<style lang="scss" scoped>
.van-tabs {
  width: 90%;
  margin: auto;
  margin-top: -20px;
  z-index: 1;
}

.van-nav-bar {
  height: 65px;
  line-height: 65px;
  background-color: #377fed;
  color: #fff;
  padding-bottom: 20px;
}
.van-nav-bar__title {
  color: #fff;
}

.van-nav-bar__right {
  top: 0px;
}
.van-tabs--line .van-tabs__wrap {
  border-radius: 4px;
}
</style>
