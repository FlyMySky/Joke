<template>
  <div class="register">
    <el-row type="flex" justify="center" align="middle">
      <el-col :span="8"></el-col>
      <el-col :span="8">
        <p>账号：</p>
        <el-input placeholder="请输入账号" prefix-icon="el-icon-email" type="email" v-model="inputTxt"></el-input>
      </el-col>
      <el-col :span="8"></el-col>
    </el-row>
    <el-row type="flex" justify="center" align="middle">
      <el-col :span="8"></el-col>
      <el-col :span="8">
        <p>密码：</p>
        <el-input placeholder="请输入密码" prefix-icon="el-icon-email" type="password" v-model="inputPsd"></el-input>
      </el-col>
      <el-col :span="8"></el-col>
    </el-row>
    <el-row type="flex" justify="center" align="middle">
      <el-col :span="8"></el-col>
      <el-col :span="8">
        <p>密码：</p>
        <el-input placeholder="请输入密码" prefix-icon="el-icon-email" type="password" v-model="inputPsd2"></el-input>
      </el-col>
      <el-col :span="8"></el-col>
    </el-row>
    <el-row type="flex" justify="center" align="middle">
      <el-col :span="8"></el-col>
      <el-col :span="8">
        <p>名称：</p>
        <el-input placeholder="请输入名称" prefix-icon="el-icon-email" type="text" v-model="inputName"></el-input>
      </el-col>
      <el-col :span="8"></el-col>
    </el-row>
      <el-row type="flex" justify="center" align="middle">
            <el-col :span="8"></el-col>
            <el-col :span="8">
                <el-button v-on:click="registerBtn">注册</el-button>
            </el-col>
            <el-col :span="8"></el-col>
        </el-row>
  </div>
</template>

<script>
import { Loading } from 'element-ui'
export default {
  name: 'Register',
  data () {
    return {
      inputTxt: '',
      inputPsd: '',
      inputPsd2: '',
      inputName: '',
      options: {
        fullscreen: true
      }
    }
  },
  methods: {
    registerBtn: function () {
      let loadingInstance = Loading.service(this.options)
      this.$nextTick(() => { // 以服务的方式调用的 Loading 需要异步关闭
        loadingInstance.close()
      })
    }
  }
}
</script>

<style scoped>
  .register {
    text-align: center;
  }

  .el-row{
    margin: 20px;
  }
  p{
    margin: 10px;
  }
  .el-button{
    width: 200px;
  }
</style>
