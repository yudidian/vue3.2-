<template>
  <div class="login">
    <el-form
      label-position="top"
      label-width="100px"
      :model="formData"
      class="login-login"
    >
      <h2>登录页面</h2>
      <el-form-item label="用户名">
        <el-input
          size="large"
          v-model="formData.name"
          class="login-input"
          placeholder="请输入用户名"
          :prefix-icon="UserFilled"
        ></el-input>
      </el-form-item>
      <el-form-item label="密码">
        <el-input
          size="large"
          v-model="formData.password"
          class="login-input"
          type="password"
          placeholder="请输入密码"
          show-password
          :prefix-icon="Unlock"
        ></el-input>
      </el-form-item>
      <el-button type="primary" size="medium" class="login-btn">登录</el-button>
    </el-form>
  </div>
</template>

<script setup>
import { reactive } from 'vue'
import { Unlock, UserFilled } from '@element-plus/icons-vue'
const formData = reactive({
  name: '',
  password: ''
})
</script>

<style scoped lang="scss">
.login {
  width: 100%;
  height: 100%;
  background-color: #2B3A4B;
  position: relative;
  .login-login {
    width: 460px;
    height: 300px;
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    text-align: center;
    h2 {
      color: white;
      text-align: center;
      font-size: 32px;
    }
    .login-btn{
      width: 240px;
      height: 46px;
      margin: 0 auto;
      font-size: 24px;
    }
    .login-input {
      &::v-deep .el-input__inner {
        background-color: #273443;
        color: white;
      }
    }
  }
}
</style>
