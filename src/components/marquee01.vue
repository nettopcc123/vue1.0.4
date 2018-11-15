<template>
<div class="marquee">

      <div class="marquee_title">
                 <span>竞彩新闻</span>
      </div>
        <div class="marquee_box">
                <ul class="marquee_list" :class="{marquee_top:animate}">
                      <li v-for="(item,index) in marqueeList">
                        <router-link :to="{ name: 'newsMore1', params: { url: item.url}}"> 
                          {{item.name}}
                        </router-link>
                        </li>
                </ul>
        </div>
</div>
</template> 
<script>
export default {
  data() {
    return {
      animate: false,

      marqueeList: [
        {
          name: "苏宁下赛季主场球衣曝光,江苏球迷喜欢这款吗?",
          url: "http://tiyu.baidu.com/news/detail/06d3e666f7b5eff99d107bc50081bee0"
        },

        {
          name: "NBA:休斯顿火箭 VS 金州勇士",
          url: "http://tiyu.baidu.com/news/detail/4b6c5d590da42b29d80f70dcd3588b0b"
        },

        {
          name: "苏珊娜-迪内奇:英超最有权势的女人",
          url: "http://tiyu.baidu.com/news/detail/5c5b01756c5f3c407a31335522313b02"
        },

        {
          name: "替伤员,米兰要租借迪亚瓦拉",
          url: "http://tiyu.baidu.com/news/detail/62606680489955196a03cc437ab834b1"
        }
      ]
    };
  },
  created: function() {
    // 页面显示
    setInterval(this.showMarquee, 2000);
  },
  methods: {
    showMarquee: function() {
      this.animate = true;

      setTimeout(() => {
        this.marqueeList.push(this.marqueeList[0]);

        this.marqueeList.shift();

        this.animate = false;
      }, 500);
    }
  }
};
</script>
 
<style lang="scss" scoped>
@import "scss/base.scss";
.marquee {
  width: 100%;

  height: 50px;

  align-items: center;

  color: #3a3a3a;

  background-color: white;

  display: flex;

  box-sizing: border-box;

  overflow: hidden;
}

.marquee_title {
  padding: 0 20px;

  height: 21px;

  font-size: 14px;

  border-right: 1px solid #d8d8d8;

  align-items: center;
}

.marquee_box {
  display: block;

  position: relative;

  width: 60%;

  height: 30px;

  overflow: hidden;
}

.marquee_list {
  display: block;

  position: absolute;

  top: 0;

  left: 0;
}

.marquee_top {
  transition: all 0.5s;

  margin-top: -30px;
}

.marquee_list li {
  height: 30px;

  line-height: 30px;

  font-size: 14px;

  padding-left: 20px;
}

.marquee_list li span {
  padding: 0 2px;
}
.marquee_list li a {
  color:#3d3d3d;
}
</style>