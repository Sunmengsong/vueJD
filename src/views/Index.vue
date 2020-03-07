<template>
  <div class="content">
    <indexSearch></indexSearch>
    <indexFooter></indexFooter>
    <!--  滚轮事件   划出侧边导航栏 -->
    <div id="side_nav">
      <ul id="sUl">
        <li>
          <a href="#recommendBig">京东秒杀</a>
        </li>
        <li>
          <a href="#show_1">特色优选</a>
        </li>
        <li>
          <a href="#show_2">频道广场</a>
        </li>
        <li>
          <a href="#show_3">客服</a>
        </li>
        <li>
          <a href="#show_4">反馈</a>
        </li>
        <li>
          <a href="javascript:;">顶部</a>
        </li>
      </ul>
    </div>
    <div>
      <carousel></carousel>
    </div>
  </div>
</template>

<script>
import indexSearch from "../components/index-search";
import indexFooter from "../components/indexFooter";
import carousel from "../components/index/carousel";
export default {
  data() {
    return {};
  },
  components: {
    indexSearch,
    indexFooter,
    carousel
  },
  beforeMount() {
    console.log(this);
  },
  methods: {
    listScroll() {
      window.addEventListener("scroll", function() {
        var scrollTop = 0;
        var sUl = document.getElementById("sUl");
        var lis = Array.from(document.querySelectorAll("#sUl>li"));
        var li = document.querySelector("#sUl>li:last-child");
        window.onscroll = function() {
          scrollTop =
            document.body.scrollTop || document.documentElement.scrollTop;
          if (scrollTop > 200) {
            sUl.style.display = "block";
          } else {
            sUl.style.display = "none";
          }
        };
        li.onclick = function(e) {
          e.preventDefault();
          var distance = scrollTop;
          var totalTime = 400;
          var steps = 50;
          var step = distance / steps;
          var interval = totalTime / steps;
          var timer = setInterval(function() {
            window.scrollBy(0, -step);
            steps--;
            if (steps == 0) {
              clearInterval(timer);
              steps = 50;
            }
          }, interval);
        };
      });
    }
  },
  created() {
    this.listScroll();
  }
};
</script>

<style>
.content {
  background-color: #f4f4f4;
  height: 3000px;
}

/* 滚轮事件   划出侧边导航栏 */
#side_nav > ul {
  width: 35px;
  height: 400px;
  position: fixed;
  bottom: 100px;
  right: 15%;
  display: none;
}
#side_nav > ul > li {
  width: 35px;
  border-bottom: 1px solid #e5e5e5;
}

#side_nav > ul > li a {
  display: block;
  width: 35px;
  height: 40px;
  font-size: 12px;
  color: #000;
  text-align: center;
}
#side_nav > ul > li:last-child {
  background-color: #000;
}
#side_nav > ul > li:last-child a {
  color: #fff;
}
#side_nav > ul > li a:hover {
  background-color: green;
  color: #fff;
}
</style>