<template>

    <div>
    <h1>登录</h1>
    <input type="text" placeholder="请输入账号" v-model="username">
    <input type="password" placeholder="请输入密码" v-model="password">
    <button @click="login">登录</button>
    <button @click="test">test</button>
  </div>

  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Axios from "axios"
Axios.defaults.baseURL='/api'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  methods: {
    test: function () {
      this.axios({
    url : '/users/hsl',
    method : 'GET',
        // 设置请求头 Authorization 的值为 token
        headers : {
          Authorization : localStorage.getItem('token')
        }
  }).then(res => {
    console.log(res);
    // 跳转到 /users/hsl 页面
    // this.$router.push('/users/hsl');
  }).catch(err => {
    console.log(err);
  })
    },
    login: function () {
      this.axios({
   url : '/users2/hsl',
   method : 'GET',
 }).then(res => {
   console.log(res);
        // 获取响应头中的authorization字段
        const token = res.headers.authorization;
        // 保存token到本地存储中
        localStorage.setItem('token',token);

   // 跳转到首页
   // this.$router.push('/home');
   alert('登录成功')
 }).catch(err => {
   console.log(err);
  })
    }
  }
}
</script>


