<template>
  <div>
    <div class="loginHtml">
      <div class="logo">
        <img src="../assets/logo.png" alt />
        <b>欢迎登录</b>
      </div>
      <a class="head_right" href>
        <i class="iconfont icon-tubiaozhizuomoban"></i>
        登录页面，调查问卷
      </a>
    </div>
    <div class="yinsi">
      <i class="iconfont icon-weibiaoti-"></i>
      依据《网络安全法》，为保障您的账户安全和正常使用，请尽快完成手机号验证！ 新版
      <a href>《京东隐私政策》</a> 已上线，将更有利于保护您的个人隐私。
    </div>
    <div class="login_model">
      <div class="loginHtml">
        <div>
          <img src="../assets/login/login_bg.png" alt />
        </div>
        <div class="loginForm">
          <div class="formHead">
            <i class="iconfont icon-weibiaoti-"></i>
            京东不会以任何理由要求您转账汇款，谨防诈骗。
          </div>
          <div class="formS" :class="isChecked==0?'checked':''">
            <a href="javascript:;" @click="changeLogin()">扫码登录</a>
          </div>
          <div class="formZ" :class="isChecked==1?'checked':''">
            <a href="javascript:;" @click="changeLogin()">账户登录</a>
          </div>
          <div>
            <div class="formSB" :style="sStyle">
              <div class="erweima" @mouseenter="showHelp()" @mouseleave="hideHelp()">
                <img src="../assets/login/show.png" />
              </div>
              <div class="erweima_help" :style="erHelpStyle">
                <img src="../assets/login/phone-orange.png" alt />
              </div>
              <div>
                <p style="position:absolute;top:200px;left:105px;color:#000">
                  打开
                  <a href="javascript:;" style="color:red;text-decoration:none">手机京东</a>&nbsp;&nbsp;&nbsp;扫描二维码
                </p>
              </div>
              <div class="erWeiFoot" style="display:flex;position:absolute;top:235px;left:65px">
                <div>
                  <i class="iconfont icon-shuru"></i>免输入
                </div>
                <div>
                  <i class="iconfont icon-icon"></i>更快
                </div>
                <div>
                  <i class="iconfont icon-yunongtongqingshuruyanzhengma"></i>更安全
                </div>
              </div>
            </div>
            <div class="formZB" :style="zStyle">
              <div class="errMsg">{{errMsg}}</div>
              <div>
                <i class="iconfont icon-04"></i>
                <input type="text" placeholder="邮箱/用户名/登录手机" v-model="uname" />
              </div>
              <div class="passWd">
                <i class="iconfont icon-mima"></i>
                <input type="password" placeholder="密码" v-model="upwd" />
              </div>
              <div class="forgetPwd">
                <a href="javascript:;">忘记密码</a>
              </div>
              <div class="loginBtn">
                <a href="javascript:;" @click="doLogin">登录</a>
              </div>
            </div>
          </div>
          <div class="loginFoot">
            <ul>
              <li>
                <i class="iconfont icon-qq"></i>
                <a href="javascript:;">QQ</a>
                <span style="margin:0 10px">|</span>
              </li>
              <li>
                <i class="iconfont icon-weixin"></i>
                <a href="javascript:;" style="margin-left:5px">微信</a>
              </li>
              <li class="regLi">
                <router-link to="reg">立即注册</router-link>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
    <div class="loginFooter">
      <div class="links">
        <a href="javascript:;">关于我们</a> |
        <a href="javascript:;">联系我们</a> |
        <a href="javascript:;">人才招聘</a> |
        <a href="javascript:;">商家入驻</a> |
        <a href="javascript:;">广告服务</a> |
        <a href="javascript:;">手机京东</a> |
        <a href="javascript:;">友情链接</a> |
        <a href="javascript:;">销售联盟</a> |
        <a href="javascript:;">京东社区</a> |
        <a href="javascript:;">京东公益</a> |
        <a href="javascript:;">English Site</a>
      </div>
      <div class="copyright">Copyright © 2004-2020 京东JD.com 版权所有</div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      sStyle: { display: "none" },
      zStyle: { display: "block" },
      // 切换登录模式
      isChecked: 1,
      // 切换登录模式函数
      // 二维码帮助样式
      erHelpStyle: { display: "none" },
      t: "",
      uname: "",
      upwd: "",
      errMsg: ""
    };
  },
  methods: {
    doLogin() {
      // console.log(this.$store.state.isLogin);
      // 发送请求, 获取数据库中用户名
      if (this.uname == "doudou" && this.upwd == "123456") {
        this.$store.commit("login");
        // console.log(this.$store.state.isLogin);
        this.$router.replace({ path: "/" });
      } else {
        this.errMsg = "用户名或密码错误";
      }
    },
    changeLogin() {
      if (this.isChecked) {
        this.isChecked = 0;
        this.sStyle["display"] = "block";
        this.zStyle["display"] = "none";
      } else {
        this.isChecked = 1;
        this.sStyle["display"] = "none";
        this.zStyle["display"] = "block";
      }
    },
    showHelp() {
      clearInterval(this.t);
      this.t = setInterval(() => {
        this.erHelpStyle["display"] = "block";
      }, 400);
    },
    hideHelp() {
      clearInterval(this.t);
      this.t = setInterval(() => {
        this.erHelpStyle["display"] = "none";
      }, 0);
    }
  }
};
</script>

<style scoped>
/* 头部 */
.icon-tubiaozhizuomoban {
  color: red;
}
.loginHtml {
  width: 990px;
  margin: 0 auto;
  position: relative;
}
.logo {
  width: 300px;
  height: 60px;
  margin: 10px 0;
  position: relative;
}
.head_right {
  position: absolute;
  right: 30px;
  top: 35px;
  color: #999;
}
b {
  position: absolute;
  right: 0;
  bottom: 0;
  font-size: 25px;
  color: #000;
}
.head_right:hover {
  color: red;
}
/* 隐私政策 */
.yinsi {
  background-color: #fff8f0;
  text-align: center;
  padding: 10px 0;
}
/* 登录主体 */
.login_model {
  background-color: #e93854;
}
.loginForm {
  position: absolute;
  width: 340px;
  top: 25px;
  right: 30px;
  background-color: #fff;
}
/* 扫码登录 */
.formSB {
  height: 233px;
  padding: 20px 19px;
  position: relative;
}
.erweima {
  width: 147px;
  height: 147px;
  padding: 8px;
  border: 1px solid #f4f4f4;
  position: absolute;
  left: 88px;
  transition: left 0.5s;
}
.erweima:hover {
  left: 20px;
}
.erweima_help {
  position: absolute;
  right: 0;
}
/* 二维码底部 */
.erWeiFoot div + div {
  margin-left: 30px;
}
.formHead {
  text-align: center;
  background-color: #fff8f0;
  padding: 10px 0;
}
.formS,
.formZ {
  width: 50%;
  display: inline-block;
  text-align: center;
  align-items: center;
  padding: 14px 0;
  border-bottom: 2px solid #f4f4f4;
}
.formS a,
.formZ a {
  display: block;
  width: 100%;
  font-size: 18px;
  text-decoration: none;
  font-family: "microsoft yahei";
}
.formS a {
  border-right: 1px solid #f4f4f4;
}
.formZ a {
  border-left: 1px solid #f4f4f4;
}
.formS a:hover,
.formZ a:hover {
  font-weight: bolder;
  color: #e4393c;
}
.checked a {
  font-weight: bolder;
  color: #e4393c;
}
.formZB .iconfont {
  display: inline-block;
  width: 38px;
  height: 38px;
  text-align: center;
  line-height: 33px;
  border: 1px solid #bdbdbd;
  border-right: 0;
  background-color: lightgray;
  margin-left: 27px;
}
.formZB .passWd {
  margin-top: 30px;
}
.formZB input {
  width: 224px;
  display: inline-block;
  height: 18px;
  line-height: 18px;
  border: 1px solid #bdbdbd;
  outline: 0;
  padding: 10px 0 10px 20px;
  font-size: 14px;
}
.errMsg {
  height: 18px;
  line-height: 18px;
  font-size: 14px;
  color: #e4393c;
  text-align: center;
  margin: 10px 0;
}
/* 忘记密码样式 */
.forgetPwd {
  width: 262px;
  margin: 20px auto;
  text-align: right;
}
.forgetPwd a:hover {
  color: #e4393c;
}
/* 登录按钮 */
.loginBtn {
  width: 302px;
  margin: 0 auto;
  padding-bottom: 30px;
}
.loginBtn a {
  display: block;
  width: 302px;
  height: 31px;
  background-color: #e4393c;
  line-height: 31px;
  padding: 5px 0;
  color: #fff;
  text-decoration: none;
  text-align: center;
  letter-spacing: 20px;
  font-size: 20px;
}
/* 登录表单底部 */
.loginFoot {
  width: 300px;
  line-height: 50px;
  border-top: 1px solid #f4f4f4;
  background-color: #fcfcfc;
  padding: 0 20px;
}
.loginFoot ul li {
  display: inline-block;
}
.loginFoot a:hover {
  color: #e93854;
}
.regLi {
  margin-left: 125px;
}
.regLi a {
  color: #b61d1d;
  font-size: 14px;
}
/* 页脚相关链接 */
.loginFooter {
  width: 990px;
  margin: 20px auto 0;
  text-align: center;
  color: #666;
}
.links {
  margin-bottom: 20px;
}
.links a {
  margin: 0 10px;
}
.links a:hover {
  color: #e4393c;
}
</style>