<template>
  <div id="register">
    <h4>用户名</h4>
    <input v-model="username" placeholder="输入要注册的用户名"></input>
    <h4>密码</h4>
    <input v-model="password" type="password" placeholder="输入要设置的密码" @keyup.enter="onRegister"></input>
    <el-button size="medium" @click="onRegister">立即注册</el-button>
    <p class="notice">已有账号？<router-link to="/login">立即登录</router-link></p>
  </div>
</template>

<script>
import { mapActions } from 'vuex'

export default {
  data () {
    return {
      username: '',
      password: ''
    }
  },

  methods: {
    ...mapActions(['register']),

    onRegister () {
      this.register({ username: this.username, password: this.password })
        .then(() => {
          this.$router.push({path: '/'})
        })
    }
  }
}
</script>

<style lang="less" scoped>
@import url('../../assets/base.less');

#register {
  display: grid;
  justify-content: center;
  padding-top: 30px;

  h4 {
    margin: 10px 0 5px;
  }

  p {
    margin: 5px 0;
  }

  input {
    width: 300px;
  }

  .error {
    font-size: 12px;
    color: #f00;
  }

  button {
    margin-top: 30px;
    justify-self: start;
  }

  .notice {
    font-size: 12px;
    color: @textLighterColor;
    text-align: center;
    margin-top: 30px;

    a {
      color: @themeColor;
    }
  }
}
</style>
