<template>
   <div class="container">

        <div id="vsb_content" style="width:60%;  margin-left:270px">
          <p class="vsbcontent_start" style="margin-bottom: 0px; font-size: 14pt; font-family: 微软雅黑; white-space: normal; font-weight: bold; padding-bottom: 0px; padding-top: 0px; padding-left: 0px; margin-top: 0px; line-height: 33px; padding-right: 0px; background-color: rgb(255,255,255)">尊敬的来信人：</p>
          <p style="margin-bottom: 0px; font-size: 12pt; font-family: 微软雅黑; white-space: normal; padding-bottom: 0px; padding-top: 0px; padding-left: 0px; margin-top: 0px; line-height: 33px; padding-right: 0px; background-color: rgb(255,255,255); text-indent: 2em">您好！</p>
          <p style="margin-bottom: 0px; font-size: 12pt; font-family: 微软雅黑; white-space: normal; padding-bottom: 0px; padding-top: 0px; padding-left: 0px; margin-top: 0px; line-height: 33px; padding-right: 0px; background-color: rgb(255,255,255); text-indent: 2em">感谢您向本网站提出您宝贵的建议。因为此网站还在测试运行中，难免有些地方做的不好。</p>
          <p style="margin-bottom: 0px; font-size: 12pt; font-family: 微软雅黑; white-space: normal; padding-bottom: 0px; padding-top: 0px; padding-left: 0px; margin-top: 0px; line-height: 33px; padding-right: 0px; background-color: rgb(255,255,255); text-indent: 2em">您的每一封来信，对我来说都十分宝贵，我初来咋到，经验不足，很多地方会出现遗漏或出现重大的Bug。所以急需您的宝贵的建议。</p>
          <p style="margin-bottom: 0px; font-size: 12pt; font-family: 微软雅黑; white-space: normal; padding-bottom: 0px; padding-top: 0px; padding-left: 0px; margin-top: 0px; line-height: 33px; padding-right: 0px; background-color: rgb(255,255,255); text-indent: 2em">您的每一封来来信都会经过仔细的研究，并且将会及时回复。</p>
          <p style="margin-bottom: 0px; font-size: 12pt; font-family: 微软雅黑; white-space: normal; padding-bottom: 0px; padding-top: 0px; padding-left: 0px; margin-top: 0px; line-height: 33px; padding-right: 0px; background-color: rgb(255,255,255); text-indent: 2em">对于提出的重大漏洞或问题，我们给予一定的奖励。</p>
          <p style="margin-bottom: 0px; font-size: 12pt; font-family: 微软雅黑; white-space: normal; padding-bottom: 0px; padding-top: 0px; padding-left: 0px; margin-top: 0px; line-height: 33px; padding-right: 0px; background-color: rgb(255,255,255); text-indent: 2em">感谢您对本网站的支持与建议！热情欢迎您为学校本网站的发展提出宝贵意见建议！</p>
          <p class="vsbcontent_end" style="margin-bottom: 0px; font-size: 13pt; font-family: 微软雅黑; white-space: normal; padding-bottom: 0px; text-align: right; padding-top: 0px; padding-left: 0px; margin-top: 0px; line-height: 33px; padding-right: 0px; background-color: rgb(255,255,255)">XuYangYang</p>
      </div>


     <div>
<el-form ref="form" :model="form" label-width="80px" style="margin-left:300px; margin-top:100px;">
  <el-form-item label="您的称呼" style="width:30%">
    <el-input v-model="form.name"></el-input>
  </el-form-item>
<el-form ref="form" :model="form" label-width="80px">
  <el-form-item label="您的email"   style="width:30%">
    <el-input v-model="form.email"></el-input>
  </el-form-item>
  <el-form-item label="您的建议" style="width:60%">
    <el-input type="textarea" v-model="form.desc" resize="none" :rows="12" ></el-input>
  </el-form-item>
  <el-form-item>
    <el-button type="primary" @click="onSubmit">提交</el-button>
  </el-form-item>
</el-form>
</el-form>
</div>
  </div>

</template>
<script>
  export default {
    data() {
      return {
        form: {
          name: '',
          email:'',
          desc: ''
        }
      }
    },
    methods: {
      onSubmit() {
        alert('邮件正在发送请稍后')
          axios.get('http://localhost:8080/Email/Sub/'+this.form.name+'/'+this.form.email+'/'+this.form.desc).then(function (resp) {
              if(resp.data.status==1){
                alert('发送成功')

              }
              else{
                alert('发送失败，请稍后再试')
              }
            })
      }
    }
  }
</script>