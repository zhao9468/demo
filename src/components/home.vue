<template>
  <div>
    <el-container class="container">
      <el-header>
        <el-row>
          <el-col :span="4">
            <img src="../assets/logo.png" alt="图片加载失败">
          </el-col>
          <el-col :span="19" class="middle">
            <h2>电商后台管理系统</h2>
          </el-col>
          <el-col :span="1">
            <a href="#" class="logout" @click="handleLoginout()">退出</a>
          </el-col>
        </el-row>
      </el-header>
      <el-container>
        <el-aside class="aside" width="200px">
          <el-row class="tac">
            <el-col>
              <el-menu unique-opened router default-active="2" class="el-menu-vertical-demo">
                <el-submenu index="1">
                  <template slot="title">
                    <i class="el-icon-location"></i>
                    <span>用户管理</span>
                  </template>
                  <el-menu-item-group>
                    <el-menu-item index="1-1">
                      <i class="el-icon-menu"></i>用户列表
                    </el-menu-item>
                  </el-menu-item-group>
                </el-submenu>
                <el-submenu index="2">
                  <template slot="title">
                    <i class="el-icon-location"></i>
                    <span>权限管理</span>
                  </template>
                  <el-menu-item-group>
                    <el-menu-item index="1-1">
                      <i class="el-icon-menu"></i>角色列表
                    </el-menu-item>
                    <el-menu-item index="1-1">
                      <i class="el-icon-menu"></i>权限列表
                    </el-menu-item>
                  </el-menu-item-group>
                </el-submenu>
                <el-submenu index="3">
                  <template slot="title">
                    <i class="el-icon-location"></i>
                    <span>商品管理</span>
                  </template>
                  <el-menu-item-group>
                    <el-menu-item index="1-1">
                      <i class="el-icon-menu"></i>商品列表
                    </el-menu-item>
                    <el-menu-item index="1-1">
                      <i class="el-icon-menu"></i>分类参数
                    </el-menu-item>
                    <el-menu-item index="1-1">
                      <i class="el-icon-menu"></i>商品分类
                    </el-menu-item>
                  </el-menu-item-group>
                </el-submenu>
                <el-submenu index="4">
                  <template slot="title">
                    <i class="el-icon-location"></i>
                    <span>订单管理</span>
                  </template>
                  <el-menu-item-group>
                    <el-menu-item index="1-1">
                      <i class="el-icon-menu"></i>订单列表
                    </el-menu-item>
                  </el-menu-item-group>
                </el-submenu>
                <el-submenu index="5">
                  <template slot="title">
                    <i class="el-icon-location"></i>
                    <span>数据统计</span>
                  </template>
                  <el-menu-item-group>
                    <el-menu-item index="1-1">
                      <i class="el-icon-menu"></i>数据报表
                    </el-menu-item>
                  </el-menu-item-group>
                </el-submenu>
              </el-menu>
            </el-col>
          </el-row>
        </el-aside>
        <el-main class="main">Main</el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script>
export default {
  methods: {
    //退出功能
    handleLoginout() {
      //清除token
      localStorage.clear();
      //来到登录
      this.$router.push({
        name: "login"
      });
      //提示
      this.$message.warning("退出成功");
    }
  },
  beforeMount() {
    if (!localStorage.getItem("token")) {
      this.$router.push({
        name: "login"
      });
      this.$message.warning("请先登录");
    }
  },
  mounted() {}
};
</script>

<style>
.container {
  background-color: #b3c0d1;
}
.aside {
  background-color: green;
  height: 1000px;
}
.main {
  background-color: yellow;
  height: 1000px;
}
.middle {
  line-height: 60px;
  text-align: center;
  color: #fff;
}
.logout {
  line-height: 60px;
  text-decoration: none;
}
</style>
