<template>
  <el-menu :router="true" default-active="1" class="el-menu-demo" mode="horizontal">
    <el-menu-item index="home">
      <el-button type="primary">Registra tu negocio</el-button>
    </el-menu-item>
    <el-menu-item index="about">Acerca de nosotros</el-menu-item>
    <el-menu-item index="register">Inicio</el-menu-item>
  </el-menu>
</template>

<script>
    export default {
        name: "NavBar"
    }
</script>

<style lang="scss">
  .el-menu-demo{
    .el-menu-item{
      float: right;
    }
  }
</style>
