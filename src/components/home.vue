<template>
  <div>
    <el-container class="container">
      <el-header>Header</el-header>
      <el-container>
        <el-aside class="aside" width="200px">Aside</el-aside>
        <el-main class="main">Main</el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script>
export default {};
</script>

<style>
.container {
  background-color: red;
}
.aside {
  background-color: green;
}
.main {
  background-color: yellow;
}
</style>
