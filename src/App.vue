<template>
  <div id="app">
    <el-container>

   <el-menu :default-active="activeIndex" class="el-menu-demo" mode="horizontal" @select="handleSelect">
    <el-menu-item style="margin-left:200px;"><router-link to="/" style="font-size:25px;font-weight:bolder;color:#4d444f;line-height:25px margin-left:20px;">XuYangYang</router-link></el-menu-item>
   <el-menu-item style="margin-left:520px; margin-top:10px;"></el-menu-item>
  <el-menu-item index="1" style="margin-right:30px;"><router-link to="/">首页</router-link></el-menu-item>
   <el-menu-item index="2" style="margin-right:30px;"><router-link to="/tags">标签</router-link></el-menu-item>
    <el-menu-item index="3" style="margin-right:30px;"><router-link to="/email">反馈</router-link></el-menu-item>
     <el-menu-item index="4" style="margin-right:30px;"><router-link to="/about">关于</router-link></el-menu-item>
     <el-menu-item index="5" style="margin-right:30px;"><router-link to="/dashboard">后台</router-link></el-menu-item>
</el-menu>
</el-container>

<div><router-view></router-view></div>
  </div>


</template>

<script>
export default {
  name: 'App',
      data() {
      return {
        activeIndex: '1',
        activeIndex2: '1'
      };
    },
    methods: {
      handleSelect(key, keyPath) {
        console.log(key, keyPath);
      }
    }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin-top: 10px;
  width: 100%;

}
  .el-header {
    text-align: center;
    line-height: 60px;
    width:100%;
  }


</style>
