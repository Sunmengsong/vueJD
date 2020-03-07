<template>
  <div>
    <div id="indexSearch">
      <div class="headBgColor">
        <div class="left">
          <span
            style="display:inline-block;padding:8px 10px"
            class="city"
            @mouseover="selectCity=true"
            @mouseout="selectCity=false"
          >北京</span>
        </div>
        <div class="right">
          <div class="rightBox">
            <div>
              <router-link to="/login">你好, 请登录</router-link>
              <router-link to="/reg" style="margin-left:5px;color:#F10215">免费注册</router-link>
            </div>|
            <div>
              <a>我的订单</a>
            </div>|
            <div>
              <a>我的京东</a>
            </div>|
            <div>
              <a>京东会员</a>
            </div>|
            <div>
              <a>企业采购</a>
            </div>|
            <div>
              <a>客户服务</a>
            </div>|
            <div>
              <a>网站导航</a>
            </div>|
            <div>
              <a>手机京东</a>
            </div>
          </div>
        </div>
      </div>
      <div v-if="selectCity" class="cityList">这是城市选择列表</div>
    </div>
    <div class="searchAndNavBg" style="background:#fff;border-bottom: 1px solid #ddd;">
      <div class="clearfix" style="width:1190px;margin:0 auto;position:relative;top:30px">
        <img src="../assets/indexBg.png" style="position:absolute;" />
        <div class="searchBar">
          <input type="text" class="searchInput" placeholder="请输入搜索的商品" label="搜索" />
          <span class="searchbtn">搜索</span>
          <span class="cart">购物车</span>
        </div>
        <div class="masNav">
          <span style="color:#f10215;font-weight:bold">秒杀</span>
          <span style="color:#f10215;font-weight:bold">优惠券</span>
          <span>PLUS会员</span>
          <span>品牌闪购</span>
          <span>拍卖</span>
          <span>京东家电</span>
          <span>京东超市</span>
          <span>京东生鲜</span>
          <span>京东国际</span>
          <span>京东金融</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selectCity: false
    };
  }
};
</script>

<style>
#indexSearch {
  background-color: #e3e4e5;
  border-bottom: 1px solid #ddd;
}
#indexSearch a {
  color: #999999;
  text-decoration: none;
  cursor: pointer;
}
#indexSearch a:hover {
  color: #f10215;
}
#indexSearch .headBgColor {
  width: 1190px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.city:hover {
  background-color: #fff;
}
.rightBox {
  display: flex;
  justify-content: space-evenly;
  align-items: center;
}
.rightBox > div {
  padding: 8px 10px;
}
.cityList {
  position: fixed;
  top: 30px;
  left: 356px;
  background: #fff;
  border: 1px solid #ddd;
  border-top-width: 0;
  padding: 20px;
  z-index: 4;
}

/* 搜索栏 */
.searchBar {
  display: flex;
  justify-content: center;
  align-items: flex-end;
  padding-top: 40px;
}
.searchBar .searchInput {
  padding: 2px 44px 2px 17px;
  border: 2px solid #e2231a;
  width: 425px;
  height: 28px;
  outline: 0;
}
.searchBar .searchbtn {
  display: inline-block;
  padding: 10px 15px;
  background-color: #e2231a;
  color: #fff;
  border: 1px solid #e2231a;
}
.searchBar .cart {
  margin-left: 20px;
  display: inline-block;
  padding: 10px 15px;
  color: #f10215;
  border: 1px solid #ddd;
}

/* 导航 */
.masNav {
  color: #000;
  font-size: 14px;
  display: flex;
  justify-content: space-around;
  width: 775px;
  margin: 30px auto;
}
.masNav > span {
  display: inline-block;
  padding: 5px 8px;
  cursor: pointer;
}
.masNav > span:hover {
  color: #f10215;
}
.clearfix::before {
  content: "";
  display: block;
  clear: both;
}
.clearfix::after {
  content: "";
  display: block;
  clear: both;
}
</style>