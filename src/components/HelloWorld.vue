<template>
  <div class="hello" v-loading="loading">
    <img src="../assets/logo.png">
    <el-row type="flex"
            justify="center"
            align="middle">
      <el-col :span="8"></el-col>
      <el-col :span="8">
        <el-input placeholder="请输入账号"
                  prefix-icon="el-icon-email"
                  type="email"
                  v-model="inputTxt"></el-input>
      </el-col>
      <el-col :span="8"></el-col>
    </el-row>
    <el-row type="flex"
            justify="center"
            align="middle">
      <el-col :span="8"></el-col>
      <el-col :span="8">
        <el-input placeholder="请输入密码"
                  prefix-icon="el-icon-password"
                  type="password"
                  v-model="inputPsd"></el-input>
      </el-col>
      <el-col :span="8"></el-col>
    </el-row>
    <el-row type="flex"
            justify="center"
            align="middle">
      <el-col :span="8"></el-col>
      <el-col v-bind:span="registerSpan">
        <el-button v-on:click="registerBtn">注册</el-button>
      </el-col>
      <el-col :span="4">
        <el-button v-on:click="loginBtn">登录</el-button>
      </el-col>
      <el-col :span="8"></el-col>
    </el-row>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      inputTxt: '',
      inputPsd: '',
      registerSpan: 4,
      loading: false
    }
  },
  methods: {
    registerBtn: function () {
      this.$router.push('/register')
    },
    loginBtn: function () {
      this.loading = true
      setTimeout(() => {
        this.loading = false
        this.$router.push('/home')
      }, 2000)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style scoped>
.el-input {
  width: 300px;
}

.el-row {
  margin: 20px;
}

.hello {
  margin-top: 60px;
}
img{
  width: 200px;
  height: 200px;
}
</style>
