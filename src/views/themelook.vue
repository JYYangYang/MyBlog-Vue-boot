<template>
<div>
    <div class="" style="margin-top:30px;">
			<div class="content">
                 <h2>{{name}}</h2>
<div class="list" v-for="item in article" :key="item">
   
            <div class="archive-post">
            <span class="uptime">{{item.createtime}}</span>
            <v-click @click="chuancan(item.id)"> {{item.title}}</v-click>
        </div>
      
    </div>
			</div><!-- content -->
			</div> <!-- /container -->
 <footer>
        <p> &copy; XuYangYang的博客 2021  <a href="www.github.com/JYYangYang">MyGitHub</a> | XuYangYang独家认证</p>
    </footer>
</div>
</template>
<script>

export default({

    methods:{
chuancan(id1){
  this.$router.push({
        path: '/Article/show/',
        query:{
          id: id1
        }
      })
},
    },
    data(){
         return{
             name:'',
         article:[{
     id:'',
            author:'',
            title:'',
            introduction:'',
            content:'',
            createtime:'',
            themes:''
         }
       
         ]
         }
    },
created(){
    const theme=this.$route.query.Theme;
     const _this= this;
      axios.get('http://localhost:8080/Article/QueryByTheme/'+theme).then(function (resp) {
         _this.article=resp.data;
         _this.name=theme
         console.log(resp)

      })
}

})
</script>

<style scoped>
  @import "../static/css/tags.css";
  @import "../static/css/public.css";
</style>
