<template>
  <div class="w" style="display:flex;">
    <div class="aside">
      <span class="asideItem" v-for="(item,index) in asideList" :key="index">
        <span class="text" v-for="(it,idx) in item.list" :key="idx">{{it}}</span>
      </span>
    </div>
    <div class="carouselBox">
      <el-carousel :interval="2000" arrow="always">
        <el-carousel-item v-for="(item,index) in carouselList" :key="index">
          <img :src="item" />
        </el-carousel-item>
      </el-carousel>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      carouselList: [
        "https://img10.360buyimg.com/babel/s590x470_jfs/t1/90966/12/13849/94449/5e5dd103E999afa6f/263c188c47d49894.jpg.webp",
        "https://imgcps.jd.com/ling/100005171461/56yU6K6w5pys57K-6YCJ5aSn54mM/5aW956S85LiN5pat/p-5bd8253082acdd181d02fa5f/565a59d4/590x470.jpg",
        "https://img14.360buyimg.com/pop/s590x470_jfs/t1/95796/4/13791/78340/5e5efa6aEab131ed7/5c8c5259348adcfd.jpg.webp",
        "https://img10.360buyimg.com/pop/s590x470_jfs/t1/101207/37/13838/81079/5e5cbef8E4c4cbbdf/c6ab7e16ecb21a14.jpg.webp",
        "https://img20.360buyimg.com/pop/s590x470_jfs/t1/85749/26/13362/98247/5e579c3eE3e78c862/7c91d105322871af.jpg.webp",
        "https://img10.360buyimg.com/pop/s590x470_jfs/t1/96750/19/13588/49315/5e5e6d50E7d324b53/489f9f45848d3cbd.jpg.webp"
      ],
      asideList: [
        {
          list: ["家用电器"]
        },
        {
          list: ["手机", "运营商", "数码"]
        },
        {
          list: ["家居", "家具", "家装", "厨具"]
        },
        {
          list: ["男装", "女装", "童装", "内衣"]
        },
        {
          list: ["美妆", "个护清洁", "宠物"]
        },
        {
          list: ["女鞋", "箱包", "钟表", "珠宝"]
        },
        {
          list: ["男鞋", "运动", "户外"]
        },
        {
          list: ["房产", "汽车", "汽车用品"]
        },
        {
          list: ["母婴", "玩具乐器"]
        },
        {
          list: ["食品", "酒类", "生鲜", "特产"]
        },
        {
          list: ["艺术", "礼品鲜花", "农资绿植"]
        },
        {
          list: ["医药保健", "计生情趣"]
        },
        {
          list: ["图书", "文娱", "教育", "电子书"]
        },
        {
          list: ["机票", "酒店", "旅游", "生活"]
        },
        {
          list: ["理财", "众筹", "白条", "保险"]
        },
        {
          list: ["安装", "维修", "清洗", "二手"]
        },
        {
          list: ["工业品"]
        }
      ]
    };
  }
};
</script>

<style>
.aside {
  display: flex;
  flex-direction: column;
  padding: 5px 0px;
  width: 190px;
  background: #fefefe;
}
.aside .asideItem {
  padding: 5px 10px;
}
.aside .asideItem:hover {
  background: #d9d9d9;
}
.aside .text {
  color: #333;
  font-size: 14px;
  margin: 5px 1px;
}
.aside .text:hover {
  text-decoration: none;
  color: #f10215;
}
.asideItem .text:not(:last-child)::after {
  content: "/";
}

.carouselBox {
  margin-left: 10px;
}
.el-carousel__container {
  width: 590px;
  height: 460px !important;
}
</style>