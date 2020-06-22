<template>
  <div class="login">
    
    <div class="left">
    
      <div class="tatle">
        <img src="@/assets/login-logo.png" alt />
        <span class="tatlename">黑马面面</span>
        <span class="tatleline">|</span>
        <span class="tatlename2">用户登录</span>
      </div>
      <el-form :model="ruleform" :rules="rules" ref="ruleform">
        <el-form-item prop="usename">
          <el-input v-model="ruleform.usename" placeholder="请输入手机号" prefix-icon="el-icon-user"></el-input>
        </el-form-item>
        <el-form-item prop="password">
          <el-input
            placeholder="请输入密码"
            v-model="ruleform.password"
            :show-password="true"
            prefix-icon="el-icon-lock"
          ></el-input>
        </el-form-item>
        <el-form-item prop="Verification">
          <el-row>
            <el-col :span="17">
              <el-input
                v-model="ruleform.Verification"
                placeholder="请输入验证码"
                prefix-icon="el-icon-key"
              ></el-input>
            </el-col>
            <el-col :span="7">
              <img src alt />
            </el-col>
          </el-row>
        </el-form-item>
        <el-form-item style="font-size:14px;" >
          <el-checkbox v-model="ruleform.checked" >
            我已阅读并同意
            <el-link type="primary">用户协议</el-link>和
            <el-link type="primary">隐私条款</el-link>
          </el-checkbox>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" class="buttn" @click="submitForm">登录</el-button>
          <br />
          <el-button type="primary" class="buttn" @click="register">注册</el-button>
        </el-form-item>
      </el-form>
    </div>
    <div class="right">e
      <img src="@/assets/login_banner_ele (1).png" alt />
    </div>
    <register ref="register"></register>
  </div>
</template>
<script>
import register from "./register.vue"
export default {
  name: "login",
  components:{
    register
  },
  data() {
    return {
      text:"",
      visible: false,
      ruleform: {
        usename: "",
        password: "",
        Verification: "",
        checked: false
      },
      rules: {
        usename: [
          { required: true, message: "请输入手机号", trigger: "blur" },
          { min: 11, max: 11, message: "请输入11位手机号", trigger: "change" }
        ],
        password: [
          { required: true, message: "请输入密码", trigger: "blur" },
          { min: 6, max: 12, message: "请输入最少6位密码", trigger: "change" }
        ],
        Verification: [
          { required: true, message: "请输入验证码", trigger: "blur" },
          { min: 4, max: 4, message: "请输入6位验证码", trigger: "blur" }
        ]
      
      }
    };
  },
  methods: {
    //登录点击
    submitForm() {
      if(this.ruleform.checked != true){
       this.$message({
          showClose: true,
          message: '请勾选用户协议',
          type: 'error'
        });
        return false;
      }
        this.$refs.ruleform.validate((valid) => {
        alert(valid);

        });
      },
      resetForm() {
        this.$refs.ruleform.resetFields();
      },
      //注册点击
      register(){
        this.$refs.register.dialogVisible=true
      }
  }
};
</script>

<style lang="less">
.login {
  display: flex;
  height: 100%;
  justify-content: space-around;
  align-items: center;
  background: linear-gradient(225deg, rgb(218, 232, 243), rgba(1, 198, 250, 1));
  .left {
   
    width: 478px;
    height: 550px;
    background: rgba(245, 245, 245, 1);
    padding: 43px;
    .popover{
      display: block;
      position: relative;
      margin: 0 auto;
      top: 50%;
      transform: translateY(-50%)  translateX(-50%);
      
    }
    .tatle {
      margin-bottom: 30px;
      .tatlename {
        font-size: 24px;
        font-family: SourceHanSansCN;
        font-weight: 400;
        color: rgba(12, 12, 12, 1);
        margin: 0 15px;
      }
      .tatleline {
        font-size: 25px;
        color: rgba(199, 199, 199, 1);
      }
      .tatlename2 {
        font-size: 22px;
        font-family: PingFangSC;
        font-weight: 400;
        color: rgba(12, 12, 12, 1);
        margin-left: 15px;
        
      }
    }
    .buttn {
      width: 100%;
    }
    .buttn:nth-child(1) {
      margin-bottom: 26px;
    }
  }
}
</style>