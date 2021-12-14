<template>
<div>
  <el-table
  
    :data="tableData"
    border
    style="width: 100%">
    <el-table-column
      prop="id"
      label="id"
      width="100">
    </el-table-column>
    <el-table-column
      prop="author"
      label="作者"
      width="100">
    </el-table-column>
    <el-table-column
      prop="title"
      label="题目"
       width="100">
    </el-table-column>
     <el-table-column
      prop="introduction"
      label="介绍"
       width="180">
    </el-table-column>
     <el-table-column
      prop="createtime"
      label="创建时间"
       width="100">
    </el-table-column>
     <el-table-column
      prop="themes"
      label="主题"
       width="100">
    </el-table-column>
      <el-table-column
      prop="Content"
      label="主要内容"
      >
    </el-table-column>
      <el-table-column
      label="操作"
      width="140"
      >
      <template slot-scope="scope">
        <el-button  @click="Delete(scope.row)" type="text" size="small">删除</el-button>
        <el-button  @click="Update(scope.row)" type="text" size="small">修改</el-button>
        <el-button @click="Look(scope.row)" type="text" size="small">查看</el-button>
      </template>
    </el-table-column>
  </el-table>

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
</template>

<script>
  export default {
 
      methods: {
        page(current){
        const _this=this;
          axios.get('http://localhost:8080/Page/ToPage/'+current+'/5').then(function (resp) {
            console.log(resp)
            _this.tableData=resp.data.page.list
            _this.total=resp.data.page.totalItemNumber
            })

      },
      handleClick(row) {
        console.log(row);
      },
       Delete(row){
            const that=this;
         axios.get('http://localhost:8080/Article/DeleteById/'+row.id).then(function (resp) {
          console.log(resp)
          that.$router.push('/JmpToList');
      })
   
      },

      Look(row){
        this.$router.push({
          path: '/Article/show/'+row.id
        })
      },
      Update(row){
        const that=this;
        that.$router.push({path:'/update',query:{id:row.id}});
      }
	  },

  

    data() {
      return {
        total: null,
        tableData: [{
          id:'',
          author:'',
          title:'',
          introduction:'',
         createtime:'',
          themes:'',
          Content:''
        }]
      }
    },
    created() {
       const _this=this;
          axios.get('http://localhost:8080/Page/ToPage/1/5').then(function (resp) {
            _this.tableData=resp.data.page.list
            _this.total=resp.data.page.totalItemNumber


            })
    }

  }
</script>