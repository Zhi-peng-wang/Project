<template>
  <div>
    <div class="panel panel-info">
      <div class="panel-heading">
        添加日志
      </div>
      <div class="panel-body">
        <h1>添加日志页面</h1>
        <div :span="24">
          <el-form label-width="80px" :model="formData">
            <el-form-item label="日志标题">
              <el-input v-model="formData.blog_title"></el-input>
            </el-form-item>
            <el-form-item label="日志类型">
              <el-input v-model="formData.region"></el-input>
            </el-form-item>
            <el-form-item label="日志内容">
              <el-input type="textarea" :rows="5" placeholder="请输入内容" v-model="formData.blog_content">
              </el-input>
            </el-form-item>
            <el-form-item>
              <el-button type="primary" >提交</el-button>
              <el-button>重置</el-button>
            </el-form-item>
          </el-form>

        </div>

      </div>
    </div>
  </div>
</template>

<script>
    export default {
      data(){
        return{
          formData: {
            blog_title: '',
            region: '',
            blog_content: ''
          }
        }
      }
    }
</script>

<style scoped>

</style>
