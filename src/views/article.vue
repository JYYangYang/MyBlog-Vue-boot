<template>
    <div class="container">
			<div class="content">
                <div class="main detail" >
    
    <h1>{{article.title}}</h1>
    
    <div class="author">{{article.author}}</div>
    
    <div class="date">创建于： {{article.createtime}}</div>
    
    <article>
        
        <div class="lead">{{article.introduction}}</div>
        
        <div v-html="article.content"></div>
    </article>

                </div>
            </div>
    </div>
</template>

<style scoped>
@import "../static/css/detail.css"; 
@import "../static/css/public.css";
</style>

<script>
import { compile } from 'path-to-regexp';

import permission from '@/directive/permission/index.js' // 权限判断指令

 export default {
 directives: { permission },
  data(){
         return{
                article:[
                    {
                        title:'服务器未连接',
                        author:'服务器未连接',
                        createtime:'服务器未连接',
                        content:'服务器未连接',
                        introduction:''
                    }
                ]
            }
  },
methods:{
    ToText(HTML)
    {
      var input = HTML;
      return input.replace(/<(style|script|iframe)[^>]*?>[\s\S]+?<\/\1\s*>/gi,'').replace(/<[^>]+?>/g,'').replace(/\s+/g,' ').replace(/ /g,' ').replace(/>/g,' ');  
    }
  },
created(){
    const id=this.$route.query.id;
     const _this= this;
      axios.get('http://localhost:8080/Article/QueryById/'+id).then(function (resp) {
         _this.article=resp.data;

      })

    
}
 }

</script>

