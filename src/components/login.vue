<template>
  <div class="login-wrap">
    <el-form class="login-form" label-position="top" label-width="80px" :model="formdata">
      <h2>用户登录</h2>
      <el-form-item label="用户名">
        <el-input v-model="formdata.username"></el-input>
      </el-form-item>
      <el-form-item label="密码">
        <el-input v-model="formdata.password"></el-input>
      </el-form-item>
      <el-button @click.prevent="handleLogin" class="login-btn" type="success">登录</el-button>
    </el-form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      formdata: {
        username: "",
        password: ""
      }
    };
  },
  methods: {
    //发送登录请求
    async handleLogin() {
      const res = await this.$http.post(`login`, this.formdata);
      const {
        data: {
          data: { token },
          meta: { msg, status }
        }
      } = res;
      //   console.log(res);
      if (status === 200) {
        //保存用户数据
        localStorage.setItem("token", token);
        // console.log(token);
        //进入home组件
        this.$router.push({
          name: "home"
        });
      } else {
        this.$message.error(msg);
      }
      // 处理异步结果
      //         .then(res => {
      //           console.log(res);
      //           const {
      //             data: {
      //               data,
      //               meta: { msg, status }
      //             }
      //           } = res;
      //           if (status === 200) {
      //             //进入home组件
      //             this.$router.push({
      //               name: "home"
      //             });
      //           } else {
      //             this.$message.error(msg);
      //           }
      //         })
      //         .catch(err => {
      //           console.log(err);
      //         });
    }
  }
};
</script>

<style>
.login-wrap {
  height: 100%;
  background-color: #324152;
  display: flex;
  justify-content: center;
  align-items: center;
}
.login-form {
  background-color: #fff;
  border-radius: 5px;
  width: 400px;
  padding: 30px;
}
.login-btn {
  width: 100%;
}
</style>
