<template>
  <div>
  <div class="container">
    <div class="content">
    <div class="tags_box">
        <a  v-for="item in article" :key="item" @click="look(item.themes)">{{item.themes}}</a>
    </div>
    </div><!-- content -->
  </div> <!-- /container -->
 <footer>
        <p> &copy; XuYangYang的博客 2021  <a href="www.github.com/JYYangYang">MyGitHub</a> | XuYangYang独家认证</p>
    </footer>
  </div>
</template>

<script>
export default {
data(){
      return {
        as:'3',
        article:[
          {
 themes:'后台服务器未连接',
          },
           
        ]
  
  }

},
methods:{
look(theme){
 this.$router.push({
        path: '/Themes/Look',
        query:{
          Theme:theme
        }
      })
}
},

created(){
   
     const _this= this;
      axios.get('http://localhost:8080/Article/QueryAllThemes').then(function (resp) {
          _this.article=resp.data;


      })
}
  }
</script>

<style scoped>
  @import "../static/css/tags.css";
  @import "../static/css/public.css";
</style>
