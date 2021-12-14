<template>
  <div class="container">
  <div class="content">
    <div class="main">
      <div class="list" style="margin-top:20px;">
        <article v-for="item in articles" :key=item style="margin-top:20px;">
          <h2 style="margin-bottom:10px;">
            <a href="" class="title"  rel="bookmark">{{item.title}}</a>
          </h2>
          <p class="description">{{item.introduction}}
           <a @click="chuancan(item.id)" class="more" title="Read More">
              <span>➥</span>Read More</a>
          </p>
          <p class="date">
            <span>posted @</span>
            <time>{{item.createtime}}</time>
          </p>
     </article>
      </div>


 <div class="page">
    <el-pagination
       background
       layout="prev, pager, next"
       page-size="5"
       :total="total"
       @current-change="page"
  >

</el-pagination>
 </div>

  </div>




  <aside class="aside">
    <div class="about">
      <h4 class="v-section-tit">About XuYangYang</h4>
      <article class="violet-about-det">
        <p>Back-end Engineer，后端开发工程师</p>
        <p>目前是一名后端开发学生，目前正在学习后端技术</p>
        <p>主要是Java后端开发</p>
        <p>坚信技术能改变世界，我们改变技术</p>
      </article>
      <p class="v-more-right">
        <router-link to="/about">
          <span>➥</span>More
          </router-link></p>
    </div>
    <div class="friendly">
      <h4 class="v-section-tit">My Links</h4>
      <article class="attent-det">
        <ul>
          <li>
            <a href="https://www.github.com/JYYangYang" target="_blank" title="my github">
              <span>GitHub</span></a>
          </li>
        </ul>
      </article>
    </div>
  </aside>

</div>
  <footer>
        <p> &copy; XuYangYang的博客 2021  <a href="www.github.com/JYYangYang">MyGitHub</a> | XuYangYang独家认证</p>
    </footer>
  </div>


</template>
<style>
@import "../static/css/index.css";
@import "../static/css/public.css";
</style>

<script>
export default {
    data() {
    return {
      total: null,
      articles: [
        {
        title:"服务器未连接",
        intro:"服务器未连接",
        time: "服务器未连接"
     },
     ]
    }
  },
  methods:{
chuancan(id1){
  this.$router.push({
        path: '/Article/show/',
        query:{
          id: id1
        }
      })
},
tiaozhuan(){
 this.$router.push({
        path: '/about',
     
      })
},
page(current){

        const _this=this;
          axios.get('http://localhost:8080/Page/ToPage/'+current+'/5').then(function (resp) {
            console.log(resp)
            _this.articles=resp.data.page.list
            _this.total=resp.data.page.totalItemNumber
            })

      }
          },

  
  created(){
    const _this=this;
          axios.get('http://localhost:8080/Page/ToPage/1/5').then(function (resp) {
            _this.articles=resp.data.page.list
            _this.total=resp.data.page.totalItemNumber
 console.log(resp)

            })
  },



}
</script>
