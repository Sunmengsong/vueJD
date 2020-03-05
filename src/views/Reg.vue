<template>
  <div>
    <div class="loginHtml">
      <div class="logo">
        <img src="../assets/logo.png" alt="">
        <b>欢迎注册</b>
      </div>
    </div>
    <div class="yinsi">
      <i class="iconfont icon-weibiaoti-"></i>
      依据《网络安全法》，为保障您的账户安全和正常使用，请尽快完成手机号验证！ 新版 <a href="">《京东隐私政策》</a> 已上线，将更有利于保护您的个人隐私。
    </div>
    <div class="formModel">
      <h1 style="text-align:center">注册</h1>
      <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="100px" class="demo-ruleForm">
        <el-form-item label="用户名" prop="name">
          <el-input v-model="ruleForm.name" placeholder="请输入用户名"></el-input>
        </el-form-item>
        <el-form-item label="密码" prop="pass">
          <el-input type="password" v-model="ruleForm.pass" autocomplete="off" placeholder="请输入密码"></el-input>
        </el-form-item>
        <el-form-item label="确认密码" prop="checkPass">
          <el-input type="password" v-model="ruleForm.checkPass" autocomplete="off" placeholder="请再次输入密码"></el-input>
        </el-form-item>
        <el-form-item
          label="手机号码"
          prop="phone"
        >
          <el-input v-enter-number type="text" maxlength="11" v-model="ruleForm.phone" autocomplete="off"
          placeholder="只能输入数字"></el-input>
        </el-form-item>
        <el-form-item label="性别" prop="resource">
          <el-radio-group v-model="ruleForm.resource">
            <el-radio label="男"></el-radio>
            <el-radio label="女"></el-radio>
          </el-radio-group>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="submitForm('ruleForm')">立即创建</el-button>
          <el-button style="margin-left:5px" @click="resetForm('ruleForm')">重置</el-button>
          <router-link to="login" class="tologin">已有账号, 去登录</router-link>
        </el-form-item>
      </el-form>
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
      <div class="copyright">
        Copyright © 2004-2020  京东JD.com 版权所有
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    var validatePass = (rule, value, callback) => {
        if (value === '') {
          callback(new Error('请输入密码'));
        } else {
          if (this.ruleForm.checkPass !== '') {
            this.$refs.ruleForm.validateField('checkPass');
          }
          callback();
        }
      };
      var validatePass2 = (rule, value, callback) => {
        if (value === '') {
          callback(new Error('请再次输入密码'));
        } else if (value !== this.ruleForm.pass) {
          callback(new Error('两次输入密码不一致!'));
        } else {
          callback();
        }
      };
      var validatePhone = (rule, value, callback) => {
        if(!(/^1(3|4|5|6|7|8|9)\d{9}$/.test(value))){
          callback(new Error('格式不正确,请输入正确的手机号'));
        }else{
          callback();
        }
      };
      return {
        ruleForm: {
          name: '',
          pass: '',
          checkPass: '',
          resource: '',
          phone: ''
        },
        rules: {
          name: [
            { required: true, message: '请输入用户名', trigger: 'blur' },
            { min: 6, max: 12, message: '长度在 6 到 12 个字符', trigger: 'blur' }
          ],
          pass: [
            { required: true, message: '请输入密码', trigger: 'blur' },
            { validator: validatePass, trigger: 'blur' }
          ],
          checkPass: [
            { required: true, message: '请再次输入密码', trigger: 'blur' },
            { validator: validatePass2, trigger: 'blur' }
          ],
          resource: [
            { required: true, message: '请选择性别', trigger: 'change' }
          ],
          phone: [
            { required: true, message: '手机号码不能为空'},
            { validator: validatePhone, trigger: 'blur' }
          ]
        }
      };
    },
    methods: {
      submitForm(formName) {
        this.$refs[formName].validate((valid) => {
          if (valid) {
            alert('submit!');
          } else {
            console.log('error submit!!');
            return false;
          }
        });
      },
      resetForm(formName) {
        this.$refs[formName].resetFields();
      },
      
    }
  }
</script>

<style>
/* 头部 */
  .icon-tubiaozhizuomoban{color:red}
  .loginHtml{
    width:990px;
    margin:0 auto;
    position: relative;
  }
  .logo{
    width:300px;height:60px;
    margin:10px 0;
    position: relative;
  }
  b{
    position: absolute;
    right: 0;bottom: 0;
    font-size: 25px;
    color:#000;
  }
  /* 隐私政策 */
  .yinsi{
    background-color: #fff8f0;
    text-align: center;
    padding:10px 0;
    box-shadow: 0px 5px 15px rgba(0,0,0,0.1)
  }
  /* 表单 */
  .formModel{
    width: 500px;margin:30px auto;
    padding:20px;
    box-shadow: 0 2px 12px 0 rgba(0, 0, 0, 0.1)
  }
  /* elementUI 输入框 */
  .el-input__inner{
    width: 75% !important;
  }
  /* 登录跳转 */
  .tologin{
    margin-left: 7px;
    font-size: 14px;
    text-decoration: none;
    color:#e93854;
  }
  /* 页脚相关链接 */
  .loginFooter{
    width:990px;border-top:1px solid #e6e6e6;
    padding-top:20px;
    margin: 20px auto 0;
    text-align: center;
    color:#666;
  }
  .links{
    margin-bottom: 20px;
  }
  .links a{
    margin:0 10px;
  }
  .links a:hover{
    color:#e4393c;
  }
</style>